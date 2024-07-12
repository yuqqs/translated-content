---
title: "SyntaxError: unterminated string literal"
slug: Web/JavaScript/Reference/Errors/String_literal_EOL
original_slug: Web/JavaScript/Reference/Errors/Unterminated_string_literal
l10n:
  sourceCommit: d71b141d2d18b96639547856714df19cefacfebf
---

{{jsSidebar("Errors")}}

Ошибка JavaScript «незавершённый строковый литерал» возникает, когда где-то встречается незавершённый [строковый литерал](/ru/docs/Web/JavaScript/Guide/Grammar_and_types#строковый_литерал). Строковые литералы должны быть заключены в одинарные (`'`) или двойные (`"`)) кавычки.

## Сообщение

```plain
SyntaxError: Unterminated string constant (Edge)
SyntaxError: unterminated string literal (Firefox)
```

## Тип ошибки

{{jsxref("SyntaxError")}}

## Что пошло не так?

Где-то есть незавершённый [строковый литерал](/ru/docs/Web/JavaScript/Guide/Grammar_and_types#строковый_литерал). Строковые литералы должны быть заключены в одинарные (`'`) или двойные (`"`) кавычки. JavaScript не делает различий между строками в одинарных и двойных кавычках. [Экранирование символов](/ru/docs/Web/JavaScript/Reference/Lexical_grammar) работают в строках, созданных и с одинарными и с двойными кавычками.

Чтобы исправить эту ошибку, проверьте:

- у вас есть открывающая и закрывающая кавычки (обе одинарные или обе двойные) для строкового литерала,
- вы правильно экранировали строковый литерал,
- строковый литерал не разбивается на несколько строк.

## Примеры

### Несколько строк

Вы не можете разделить строку на несколько строк, как в JavaScript:

```js-nolint example-bad
var longString = "Это очень длинная строка, которую
                  необходимо разбивать на несколько строк,
                  потому что иначе её трудно читать.";
// SyntaxError: unterminated string literal
```

Вместо этого используйте [оператор +](/ru/docs/Web/JavaScript/Reference/Operators/Addition), обратную косую черту или [шаблонные строки](/ru/docs/Web/JavaScript/Reference/Template_literals).

Вариант с оператором `+` выглядит следующим образом:

```js example-good
const longString =
  "Это очень длинная строка, которую " +
  "необходимо разбивать на несколько строк, " +
  "потому что иначе её трудно читать.";
```

Или можно использовать символ обратной косой черты ("\\") в конце каждой строки, чтобы указать, что текст будет продолжаться на следующей строке. Убедитесь, что после обратной косой черты нет пробелов или других символов (кроме разрыва строки) или отступа, иначе это не сработает. Такой подход выглядит следующим образом:

```js example-good
const longString =
  "Это очень длинная строка, которую \
необходимо разбивать на несколько строк, \
потому что иначе её трудно читать.";
```

Ещё одна возможность — использовать [шаблонные строки](/ru/docs/Web/JavaScript/Reference/Template_literals):

```js example-good
const longString = `Это очень длинная строка, которую
необходимо разбивать на несколько строк,
потому что иначе её трудно читать.`;
```

## Смотрите также

- [Строковый литерал](/ru/docs/Web/JavaScript/Guide/Grammar_and_types#строковый_литерал)
- [Шаблонные строки](/ru/docs/Web/JavaScript/Reference/Template_literals)
