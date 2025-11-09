## Project for Translation Error Grounding

### Dataset Description
The data files include:
- **Zhen-1080**: 1080 sentences (Chinese-English translation errors).
- **Ende-954**: 954 sentences (English-German translation errors).

Each data entry contains the following information (except for the Error Explanation, all other fields are derived from MQM manual annotation):
- **Source**: The original text in the source language.
- **Target**: The translated text in the target language.
- **Reference**: The correct or ideal translation.
- **Category**: The category of translation error (e.g., Accuracy/Mistranslation).
- **Severity**: The level of the error (e.g., minor, major).
- **Error Position**: The location of the error in the target text (highlighted with `<v>...</v>` tags).
- **Error Explanation**: A detailed description of the error and its cause, manually annotated by human annotators using standardized templates to ensure consistency and clarity.

### Explanation Templates
The explanations in the dataset are manually annotated by human annotators based on these predefined templates, categorized by error type. Placeholders like `[err]`, `[src]`, `[tgt]`, `[correction]`, `[position]`, and `[answer]` are filled based on the specific error instance. Ellipses (`......`) indicate optional contextual details.

| Error Type                  | Explanation Template |
|-----------------------------|----------------------|
| **Accuracy/Addition**      | There is no information about [err] in the source, but it is included in the translation; so, delete [err]. |
| **Accuracy/Mistranslation**| There is a translation error in the target, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Accuracy/Omission**      | There is no translation for [src]; so, it should be translated as [correction] and added [position]. |
| **Accuracy/Source language fragment** | The translation of [src] in the source is wrong; so, change [err] to [correction]. |
| **Fluency/Grammar**        | There is a grammatical error in the translation ......; so, change [err] to [answer]. |
| **Fluency/Inconsistency**  | There is an inconsistency in the translation, [src] is translated as [err] in the missing context; so, change [err] to [correction]. |
| **Fluency/Punctuation**    | There is a punctuation error in the translation, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Fluency/Register**       | There is a fluency issue in the translation that does not fit the context ......; so, change [err] to [correction]. |
| **Fluency/Spelling**       | There is a spelling error in the translation, [err] should be spelled as [tgt]; so, change [err] to [correction]. |
| **Fluency/Character encoding** | There is a garbled character in the translation; so, change [err] to [correction]. |
| **Locale convention**      | There is a format error in the translation, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Style/Awkward**          | The style of the translation does not conform to language conventions ......; so, change [err] to [correction]. |
| **Terminology**            | There is a terminology in the translation that is inappropriate for context, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Non-translation**        | It is impossible to reliably characterize distinct errors in the target, [src] should be translated as [tgt]; so, change [err] to [correction]. |

### Sample Entry
Here's an example of a data entry in YAML-like format for clarity:

```yaml
source: 又或者餐厅还要多久会准备好？可不可以帮我问下？
target: Or how long before the restaurant <v>is ready</v>? Can you ask for me?
reference: And how much longer does it take for the restaurant to prepare it? Could you help me ask them?
category: Accuracy/Mistranslation
severity: minor
explanation: There is a translation error in the target, "准备好" should be translated as "preparation is ready" in the context; so, change "is ready" to "preparation is ready".


```