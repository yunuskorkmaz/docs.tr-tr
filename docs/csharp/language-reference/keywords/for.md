---
title: deyim için - C# referans
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738802"
---
# <a name="for-c-reference"></a>for (C# referansı)

`for` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.

İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilir veya continue deyimini kullanarak döngüdeki bir sonraki yinelemeye adım atabilirsiniz. [continue](continue.md) `for` Ayrıca [goto](goto.md) `for` tarafından bir döngü çıkmak , [return](return.md), veya ifadeler [atmak.](throw.md)

## <a name="structure-of-the-for-statement"></a>İfadenin `for` yapısı

Deyim, *başharf*, *durum*ve *yineleyici* bölümleri tanımlar: `for`

```csharp
for (initializer; condition; iterator)
    body
```

Her üç bölüm isteğe bağlıdır. Döngügövdesi bir deyim veya ifadeler bloğudur.

Aşağıdaki örnek, `for` tanımlanan tüm bölümlerle ifadeyi gösterir:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Baş harf* bölümü

*Başharf* bölümündeki ifadeler döngüye girmeden önce yalnızca bir kez yürütülür. *Baş harfi* alan bölüm aşağıdakilerden biridir:

- Döngü dışından erişilmeden yerel bir döngü değişkeninin bildirimi ve başlatılması.

- Aşağıdaki listeden virgülle ayrılmış sıfır veya daha fazla ifade ifadeleri:

  - [atama](../operators/assignment-operator.md) deyimi

  - bir yöntemin çağrılması

  - önek veya postfix [artış](../operators/arithmetic-operators.md#increment-operator-) ifade, `++i` gibi veya`i++`

  - önek veya postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) `--i` ifadesi gibi veya`i--`

  - [yeni](../operators/new-operator.md) işleç kullanarak bir nesnenin oluşturulması

  - ifade [bekliyor](../operators/await.md)

Yukarıdaki örnekteki *başharf* bölümü yerel döngü değişkenini `i`bildirir ve başharfe bildirir:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Koşul* bölümü

*Durum* bölümü, varsa, bir boolean ifade olmalıdır. Bu ifade her döngü yinelemesinden önce değerlendirilir. *Koşul* bölümü yoksa veya boolean ifadesi ,bir `true`sonraki döngü yinelemesi yürütülür; aksi takdirde, döngü çıkar.

Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonunun dolup dolmadığını belirler:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Yineleyici* bölümü

*Yineleme* bölümü, döngü gövdesinin her yinelemeden sonra ne olacağını tanımlar. *Yineleyici* bölümü, virgülle ayrılmış aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:

- [atama](../operators/assignment-operator.md) deyimi

- bir yöntemin çağrılması

- önek veya postfix [artış](../operators/arithmetic-operators.md#increment-operator-) ifade, `++i` gibi veya`i++`

- önek veya postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) `--i` ifadesi gibi veya`i--`

- [yeni](../operators/new-operator.md) işleç kullanarak bir nesnenin oluşturulması

- ifade [bekliyor](../operators/await.md)

Yukarıdaki örnekteki *yineleyici* bölümü yerel döngü değişkenini oluşturur:

```csharp
i++
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, deyim `for` bölümlerinin daha az yaygın birkaç kullanımını göstermektedir: *başharf* bölümünde bir dış döngü değişkenine değer atamak, hem *başharf* hem de *yineleyici* bölümlerinde bir yöntem çağırmak ve *yineleyici* bölümündeki iki değişkenin değerlerini değiştirmek. Örnek kodu çalıştırmak için **Çalıştır'ı** seçin. Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Aşağıdaki örnekte sonsuz `for` döngü tanımlanır:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [ekstre](~/_csharplang/spec/statements.md#the-for-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [foreach, in](foreach-in.md)
