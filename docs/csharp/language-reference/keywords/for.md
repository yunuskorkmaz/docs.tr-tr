---
title: for deyimleri-C# başvurusu
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: db7cecc697a9cc9e5ff6b94b78747b799ed7e505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401907"
---
# <a name="for-c-reference"></a>for (C# Başvurusu)

`for`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` .

Deyimdeki herhangi bir noktada `for` , [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz. Ayrıca `for` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.

## <a name="structure-of-the-for-statement"></a>`for`Deyimin yapısı

`for`İfade *Başlatıcı*, *koşul*ve *Yineleyici* bölümlerini tanımlar:

```csharp
for (initializer; condition; iterator)
    body
```

Üç bölüm de isteğe bağlıdır. Döngünün gövdesi bir deyim ya da deyimler bloğu.

Aşağıdaki örnek, `for` tanımlı tüm bölümleri içeren ifadesini gösterir:

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Başlatıcı* bölümü

*Başlatıcı* bölümündeki deyimler, döngüyü girmeden önce yalnızca bir kez yürütülür. *Başlatıcı* bölümü aşağıdakilerden biri olabilir:

- Döngü dışından erişilemeyen bir yerel döngü değişkeninin bildirimi ve başlatılması.

- Aşağıdaki listeden, virgülle ayrılmış olarak sıfır veya daha fazla deyim ifadesi:

  - [atama](../operators/assignment-operator.md) ekstresi

  - bir yöntemin çağrılması

  - veya gibi ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi `++i``i++`

  - veya gibi sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi `--i``i--`

  - [New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma

  - [await](../operators/await.md) ifadesi

Yukarıdaki örnekteki *Başlatıcı* bölümü, yerel döngü değişkenini bildirir ve başlatır `i` :

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Koşul* bölümü

*Koşul* bölümü varsa, bir Boolean ifadesi olmalıdır. Bu ifade, her döngü yinelemesinden önce değerlendirilir. *Koşul* bölümü yoksa veya Boole ifadesi olarak değerlendirilirse `true` , sonraki döngü yinelemesi yürütülür; Aksi takdirde, döngüden çıkıldı.

Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonlandırdığını belirler:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Yineleyici* bölümü

*Yineleyici* bölümü, döngü gövdesinin her yinelemesinden sonra ne olacağını tanımlar. *Yineleyici* bölümü, virgülle ayrılmış olarak aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:

- [atama](../operators/assignment-operator.md) ekstresi

- bir yöntemin çağrılması

- veya gibi ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi `++i``i++`

- veya gibi sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi `--i``i--`

- [New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma

- [await](../operators/await.md) ifadesi

Yukarıdaki örnekteki *Yineleyici* bölümü, yerel döngü değişkenini artırır:

```csharp
i++
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, ifade bölümlerinin birkaç daha az ortak kullanımını göstermektedir `for` : *Başlatıcı* bölümünde bir dış döngü değişkenine değer atama, *Başlatıcı* ve *Yineleyici* bölümlerinde bir yöntemi çağırma ve *Yineleyici* bölümündeki iki değişkenin değerlerini değiştirme. Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

Aşağıdaki örnek sonsuz `for` döngüsünü tanımlar:

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [for deyimleri](~/_csharplang/spec/statements.md#the-for-statement) bölümü.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [foreach, in](foreach-in.md)
