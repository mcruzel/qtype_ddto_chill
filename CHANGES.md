# Changelog

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
