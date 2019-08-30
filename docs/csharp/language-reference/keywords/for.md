---
title: C#for deyimleri
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 61315a04ca8d5a619a3dcaf43b15a309919d3c42
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167877"
---
# <a name="for-c-reference"></a>(C# başvuru) için

Deyimi `for` , belirtilen bir Boole ifadesi olarak `true`değerlendirilen bir deyimi veya bir deyim bloğunu yürütür.

`for` Deyimdeki herhangi bir noktada, [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz. Ayrıca [goto](goto.md), [Return](return.md)veya `for` [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.

## <a name="structure-of-the-for-statement"></a>`for` Deyimin yapısı

İfade Başlatıcı, *koşul*ve *Yineleyici* bölümlerini tanımlar: `for`

```csharp
for (initializer; condition; iterator)
    body
```

Üç bölüm de isteğe bağlıdır. Döngünün gövdesi bir deyim ya da deyimler bloğu.

Aşağıdaki örnek, tanımlı tüm `for` bölümleri içeren ifadesini gösterir:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Başlatıcı* bölümü

*Başlatıcı* bölümündeki deyimler, döngüyü girmeden önce yalnızca bir kez yürütülür. *Başlatıcı* bölümü aşağıdakilerden biri olabilir:

- Döngü dışından erişilemeyen bir yerel döngü değişkeninin bildirimi ve başlatılması.

- Aşağıdaki listeden, virgülle ayrılmış olarak sıfır veya daha fazla deyim ifadesi:

  - [atama](../operators/assignment-operator.md) ekstresi

  - bir yöntemin çağrılması

  - veya gibi `++i` ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi`i++`

  - veya gibi `--i` sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi`i--`

  - [New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma

  - [await](../operators/await.md) ifadesi

Yukarıdaki örnekteki *Başlatıcı* bölümü, yerel döngü değişkenini `i`bildirir ve başlatır:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Koşul* bölümü

*Koşul* bölümü varsa, bir Boolean ifadesi olmalıdır. Bu ifade, her döngü yinelemesinden önce değerlendirilir. *Koşul* bölümü yoksa veya Boole ifadesi olarak `true`değerlendirilirse, sonraki döngü yinelemesi yürütülür; Aksi takdirde, döngüden çıkıldı.

Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonlandırdığını belirler:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Yineleyici* bölümü

*Yineleyici* bölümü, döngü gövdesinin her yinelemesinden sonra ne olacağını tanımlar. *Yineleyici* bölümü, virgülle ayrılmış olarak aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:

- [atama](../operators/assignment-operator.md) ekstresi

- bir yöntemin çağrılması

- veya gibi `++i` ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi`i++`

- veya gibi `--i` sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi`i--`

- [New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma

- [await](../operators/await.md) ifadesi

Yukarıdaki örnekteki *Yineleyici* bölümü, yerel döngü değişkenini artırır:

```csharp
i++
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, `for` ifade bölümlerinin birkaç daha az ortak kullanımını göstermektedir: *Başlatıcı* bölümünde bir dış döngü değişkenine değer atama, hem *Başlatıcı* hem de Yineleyici içinde bir yöntemi çağırmabölümler ve *Yineleyici* bölümünde iki değişkenin değerlerini değiştirme. Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Aşağıdaki örnek sonsuz `for` döngüsünü tanımlar:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminin](../language-specification/index.md) [for deyimleri](~/_csharplang/spec/statements.md#the-for-statement) bölümü.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [foreach, in](foreach-in.md)
