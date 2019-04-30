---
title: C# deyimi
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: ba156eed25f28a0568e11c986de1e84db3cd9cf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661587"
---
# <a name="for-c-reference"></a>(için C# Başvurusu)

`for` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.

Herhangi bir anda işaret içinde `for` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi veya bir sonraki yinelemesine kullanarak adım [devam](continue.md) deyimi. Ayrıca çıkış bir `for` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.

## <a name="structure-of-the-for-statement"></a>Yapısını `for` deyimi

`for` Tanımlar *Başlatıcı*, *koşul*, ve *yineleyici* bölümler:

```csharp
for (initializer; condition; iterator)
    body
```

Tüm üç bölüm isteğe bağlıdır. Döngü gövdesi bir deyimi veya bir deyimler bloğunu ' dir.

Aşağıdaki örnekte gösterildiği `for` deyimiyle tüm tanımlı bölümler:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Başlatıcı* bölümü

İfadeler *Başlatıcı* bölüm yürütülür yalnızca bir kez döngü girmeden önce. *Başlatıcı* bölümünde aşağıdakilerden birini alır:

- Döngü dışında erişilemez bir yerel Döngü değişkeninin başlatma ve bildirimi.

- Virgülle ayırarak aşağıdaki listeden sıfır veya daha fazla deyim ifadeleri:

  - [atama](../operators/assignment-operator.md) deyimi

  - bir yöntemi çağrıldı

  - ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifade gibi `++i` veya `i++`

  - ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifade gibi `--i` veya `i--`

  - kullanarak bir nesne oluşturulması [yeni](new-operator.md) anahtar sözcüğü

  - [await](await.md) ifadesi

*Başlatıcı* Yukarıdaki örnek bölümünde bildirir ve yerel Döngü değişkeninin başlatır `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Koşul* bölümü

*Koşul* bölümünde varsa olmalıdır bir boolean ifadesi. Bu ifade, her döngü yinelemesinden önce değerlendirilir. Varsa *koşul* bölümü mevcut değil ya da Boole ifadenin değerlendirdiği `true`sonraki döngü yinelemesi yürütülen; Aksi takdirde, döngü çıkıldı.

*Koşul* Yukarıdaki örnek bölümünde döngü yerel Döngü değişkeninin değerine göre kesilip kesilmediğini belirler:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Yineleyici* bölümü

*Yineleyici* bölüm tanımlar döngü gövdesinin her yinelemeden sonra ne olur. *Yineleyici* sıfır veya daha fazla virgülle ayırarak aşağıdaki deyim ifadeleri bölüm içerir:

- [atama](../operators/assignment-operator.md) deyimi

- bir yöntemi çağrıldı

- ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifade gibi `++i` veya `i++`

- ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifade gibi `--i` veya `i--`

- kullanarak bir nesne oluşturulması [yeni](new-operator.md) anahtar sözcüğü

- [await](await.md) ifadesi

*Yineleyici* Yukarıdaki örnek bölümünde yerel Döngü değişkeninin artırır:

```csharp
i++
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnekte, birkaç yaygın kullanımları daha az gösterilmektedir `for` deyimi bölümler: bir dış Döngü değişkeninin içinde bir değer atamak *Başlatıcı* bölümü, hem de bir yöntem çağırma  *Başlatıcı* ve *yineleyici* bölümler ve iki değişkenin değiştirerek *yineleyici* bölümü. Seçin **çalıştırma** örnek kodu çalıştırmak için. Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Aşağıdaki örnek, sınırsız tanımlar `for` döngü:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [deyimi için](~/_csharplang/spec/statements.md#the-for-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yineleme Deyimleri](iteration-statements.md)
- [foreach, in](foreach-in.md)
