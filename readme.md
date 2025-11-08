## Dataset for Translation Error Grounding

### Description
The data files include:
- **zhen:** 1080 Chinese-English translation errors
- **ende:** 954 English-German translation errors

Each data entry contains the following information (except for the ‘Explanation’, all fields are from MQM manual annotation of the errors [WMT 2022](http://www.statmt.org/wmt22/)):
- **Source**: The original text in the source language.
- **Target**: The translated text in the target language.
- **Reference**: Reference: The manual translation.
- **Category**: The category of the translation error (e.g., Accuracy/Mistranslation).
- **Severity**: The severity of the error (e.g., minor, major).
- **Location**: The location of the error in the target text (highlighted with `<v>...</v>` tags).
- **Explanation**: A detailed description of the error and its cause, manually annotated by human annotators using standardized templates to ensure consistency and clarity. *This is for evaluating translation error grounding.*

### Explanation Templates
The explanations in the dataset are manually annotated by human annotators based on these predefined templates, categorized by the error category. Placeholders like `[err]`, `[src]`, `[tgt]`, `[correction]`, `[position]`, and `[answer]` are filled according to the specific error instance. Ellipses (`......`) indicate optional contextual details.

| Error Type                  | Explanation Template |
|-----------------------------|----------------------|
| **Accuracy/Addition**      | There is no information about [err] in the source, but it is included in the translation; so, delete [err]. |
| **Accuracy/Mistranslation**| There is a translation error in the target, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Accuracy/Omission**      | There is no translation for [src]; so, it should be translated as [correction] and added [position]. |
| **Accuracy/Source language fragment** | The translation of [src] in the source is wrong; so, change [err] to [correction]. |
| **Fluency/Grammar**        | There is a grammatical error in the translation ......; so, change [err] to [answer]. |
| **Fluency/Inconsistency**  | There is an inconsistency in the translation, [src] is translated as [err] in the missing context; so, change [err] to [correction]. |
| **Fluency/Punctuation**    | There is a punctuation error in the translation, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Fluency/Register**       | There is a fluency issue in the translation that does not fit the context ......; so, change [err] to [correction]. |
| **Fluency/Spelling**       | There is a spelling error in the translation, [err] should be spelled as [tgt]; so, change [err] to [correction]. |
| **Fluency/Character encoding** | There is a garbled character in the translation; so, change [err] to [correction]. |
| **Locale convention**      | There is a format error in the translation, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Style/Awkward**          | The style of the translation does not conform to language conventions ......; so, change [err] to [correction]. |
| **Terminology**            | There is a terminology in the translation that is inappropriate for context, [src] should be translated as [tgt]; so, change [err] to [correction]. |
| **Non-translation**        | It is impossible to reliably characterize distinct errors in the target, [src] should be translated as [tgt]; so, change [err] to [correction]. |

### Sample Entry
Here's an example of a data entry in YAML-like format for clarity:

```yaml
source: A2系列相关宝贝如下：
target: The related <v>treasures</v> of A2 series are as follows:
reference: A2 series products are as below:
category: Accuracy/Mistranslation
severity: major
explanation: There is a translation error in the target, "宝贝" should be translated as "products" in the context; so, change "treasures" to "products".
```
