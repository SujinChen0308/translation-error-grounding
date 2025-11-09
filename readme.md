## Project for Translation Error Grounding


### Dataset Description
The data files include:
- **Zhen-1080**: 1080 sentences (Chinese-English translation errors).
- **Ende-954**: 954 sentences (English-German translation errors).

Each data entry contains the following information:
- **Source**: The original text in the source language.
- **Target**: The translated text in the target language.
- **Reference**: The correct or ideal translation.
- **Category**: The category of translation error (e.g., Accuracy/Mistranslation).
- **Severity**: The level of the error (e.g., minor, major).
- **Error Position**: The location of the error in the target text (highlighted with `<v>...</v>` tags).
- **Error Explanation**: A detailed description of the error and its cause.

### Sample Entry
Here's an example of a data entry in YAML-like format for clarity:

```yaml
source: 又或者餐厅还要多久会准备好？可不可以帮我问下？
target: Or how long before the restaurant <v>is ready</v>? Can you ask for me?
reference: And how much longer does it take for the restaurant to prepare it? Could you help me ask them?
category: Accuracy/Mistranslation
severity: minor
explanation: The target mistranslates "准备好" as "is ready," which implies the restaurant itself being ready (e.g., open). In this context, it should refer to the preparation (e.g., table or meal) being complete, so revise to "preparation is ready" for accuracy.
```