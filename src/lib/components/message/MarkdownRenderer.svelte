<script lang="ts">
  import { marked } from "marked";
  import DOMPurify from "dompurify";

  interface Props {
    text: string;
    prefix: string;
    colorClass: string;
  }

  const { text, prefix, colorClass }: Props = $props();

  const renderedHtml = $derived.by(() => {
    const raw = text ?? "";
    try {
      const html = marked.parse(raw, {
        async: false,
        breaks: true,
      }) as string;

      return DOMPurify.sanitize(html, {
        ALLOWED_TAGS: [
          "a", "p", "br", "strong", "em", "code", "pre", "blockquote",
          "ul", "ol", "li", "hr", "h1", "h2", "h3", "h4", "h5", "h6", "img",
        ],
        ALLOWED_ATTR: ["href", "title", "src", "alt"],
      });
    } catch {
      return DOMPurify.sanitize(raw);
    }
  });
</script>

<div class="flex items-start gap-sm">
  {#if prefix}<span class="prefix flex-shrink-0 font-semibold {colorClass}">{prefix}</span>{/if}
  <div class="text-cli-text min-w-0 break-words markdown">{@html renderedHtml}</div>
</div>
