
# Readwise

## Ghost Reader

### Summary

```
{#- BACKGROUND: This prompt instructs ChatGPT to summarize the document into three information-dense sentences. It's intended to be used after you're done reading. If you want your summaries in a language other than English, we recommend rewriting the entire prompt in the target language. You can get quite creative using combinations of logic and variables to enable all kinds of creative use cases. See the documentation for details and examples. -#}

As a professional summarizer following the TLDR best practice, create a concise and comprehensive summary of the provided content while adhering to these guidelines:

* Craft a summary that is detailed, thorough, in-depth, and complex, while maintaining clarity and conciseness.
* Incorporate main ideas and essential information, eliminating extraneous language and focusing on critical aspects.
{#- Make sure the summary stick to the content -#}
* Rely strictly on the provided text, without including external information. Review the articles and summary for 3 times and cross reference the accuracy of the summary.
* Explain the professional terms with clear, simple and understandable words.
* Format the summary in paragraph form for easy understanding and clear next action.
* The summary should be in tranditional Chinese

Here is the document to summary:

===
Title: {{ document.title }}
Author: {{ document.author }}
Domain: {{ document.domain}}
{#- The if-else logic below checks if the document is very long, long, or short in order to not exceed the GPT "prompt window". We highly recommend not changing this unless you know what you're doing. -#}
{% if (document.content | num_tokens) > 25000 %}
{{ document.html | central_paragraphs | join('\n\n') }}
{% elif (document.content | num_tokens) > 2500 %}
{{ document.content | central_sentences | join('\n\n') }}
{% else %}
{{ document.content }}
{% endif %}
===

IMPORTANT: Write no more than THREE sentences for each point. Each sentence should be clear, detail with take away, not just general sentences. Use words sparingly and please capture the big idea. The total characters should not be over 1000 characters.

```
