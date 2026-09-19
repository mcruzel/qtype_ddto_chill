# Changelog

## 1.0.0-alpha3

- Fix a fatal error that made every page listing the question types unusable
  (including the quiz *Questions* tab, which rendered up to that point and then
  stopped): `#[\Override]` was set on three methods that override nothing, and
  PHP 8.3 and later reject that at compile time. `compute_final_grade()` was
  unreachable dead code and has been removed; the two
  `define_question_plugin_structure()` hooks keep their bodies, without the
  attribute.
- Fix the crash when creating a question (`Non-static method
  PEAR::getStaticProperty() cannot be called statically`): the core
  `questiontext` editor is replaced by hidden fields, but
  `question_edit_form::set_data()` reads that element back whenever the question
  has no text yet, which is every new question.
- Fix the sentence being mangled when an existing question is reopened and saved
  again: the spaces around each gap were dropped, gluing words together, moving
  the gaps and sometimes removing them entirely. Questions saved twice with an
  earlier version have to be repaired by hand.
- Fix choices declared as HTML being imported with their markup baked in
  (`<b>dog</b>` became `DOG`).
- Fix the *right answer* feedback showing `[[correctansweris]]`: the string was
  read from the `question` component, which does not define it.
- Tests: the suite now runs to completion and passes on Moodle 5.0 / PHP 8.4.

## 1.0.0-alpha2

- Fix the question editing form hanging on a blank loading spinner when adding
  a question: the core `questiontext` editor is no longer rendered (and then
  hidden with `display:none`), which blocked TinyMCE/Atto `Pending` from resolving.
- Fix a PHP 8.1+ TypeError on `count($this->question->options->answers)` when
  the edit form is built for a question that only has `options->choices`.

## 1.0.0-alpha1

- First version of the autonomous `qtype_ddto_chill` question type.
- Plain-text sentence, tick detected words to make gaps, optional distractors.
- Negative marking, all-or-nothing and shuffle, same model as QCM Chill.
- Student attempt: drag-and-drop chips, with a native `<select>` fallback.
- Moodle XML import/export, backup/restore, privacy preferences.
