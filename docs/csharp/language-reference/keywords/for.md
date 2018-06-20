---
title: for (C# Başvurusu)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208420"
---
# <a name="for-c-reference"></a>(için C# Başvurusu)

`for` Deyimi, bir deyim veya ifadeleri bir blok için belirtilen bir Boole ifadesini değerlendirir sırada yürütür `true`.

Bir oranda noktası içinde `for` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) deyimi ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) deyimi. Ayrıca çıkabilirsiniz bir `for` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.
  
## <a name="structure-of-the-for-statement"></a>Yapısını `for` deyimi

`for` Deyimi tanımlar *Başlatıcı*, *koşulu*, ve *yineleyici* bölümler:
  
```csharp
for (initializer; condition; iterator)  
    body  
```

Tüm üç bölüm isteğe bağlıdır. Bir deyim veya deyimleri bloğu döngü gövdesidir.

Aşağıdaki örnekte gösterildiği `for` tüm tanımlı bölümler deyimiyle:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Başlatıcı* bölümü

İfadeler *Başlatıcı* bölüm yürütülme yalnızca bir kez döngü girmeden önce. *Başlatıcı* bölümünde aşağıdakilerden birini alır:

- Bildirim ve başlatma gelen döngü dışında erişilemez bir yerel döngü değişkenin.

- Sıfır veya daha fazla deyimi ifadeleri virgülle ayırarak aşağıdaki listeden:

  - [atama](../operators/assignment-operator.md) deyimi

  - bir yöntemi çağrıldı  

  - önek veya sonek [artırma](../operators/increment-operator.md) ifadesi gibi `++i` veya `i++`  

  - önek veya sonek [azaltma](../operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`  

  - kullanarak bir nesne oluşturulmasını [yeni](new-operator.md) anahtar sözcüğü

  - [await](await.md) ifadesi

*Başlatıcı* yukarıdaki örnekte bölümünde bildirir ve yerel döngü değişkenini `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Koşulu* bölümü

*Koşulu* bölümünde, varsa, olmalıdır Boole ifadesi. İfade, her döngü tekrarında önce değerlendirilir. Varsa *koşulu* bölüm mevcut değil ya da Boole ifadesi değerlendiren `true`sonraki döngü tekrarında yürütülen; Aksi takdirde, döngü çıkıldı.

*Koşulu* yukarıdaki örnekte bölümünde döngü yerel döngü değişkeni değere göre kesilip kesilmediğini belirler:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Yineleyici* bölümü

*Yineleyici* bölümü tanımlar ne döngüden gövdesinin her yinelemeden sonra olur. *Yineleyici* bölüm, sıfır veya daha fazla virgülle ayırarak aşağıdaki deyimi ifadeleri içerir:  

- [atama](../operators/assignment-operator.md) deyimi

- bir yöntemi çağrıldı  

- önek veya sonek [artırma](../operators/increment-operator.md) ifadesi gibi `++i` veya `i++`  

- önek veya sonek [azaltma](../operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`  

- kullanarak bir nesne oluşturulmasını [yeni](new-operator.md) anahtar sözcüğü

- [await](await.md) ifadesi

*Yineleyici* yukarıdaki örnekte bölümünde artırır yerel döngü değişkeni:

```csharp
i++
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek birçok yaygın kullanımları daha az gösterilmektedir `for` deyimi bölümleri: bir dış döngü değişken için bir değer atama *Başlatıcı* bölümünde, hem de bir yöntem çağırma  *Başlatıcı* ve *yineleyici* bölümler ve iki değişken değerlerini değiştirme *yineleyici* bölümü. Seçin **çalıştırmak** örnek kodu çalıştırmak için. Bundan sonra kodu değiştirin ve yeniden çalıştırın.
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
Aşağıdaki örnek, sonsuz tanımlar `for` döngü:
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>C# dili belirtimi  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

[Deyimi (C# dil belirtimi) için](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[C# başvurusu](../index.md)  
[C# Programlama Kılavuzu](../../programming-guide/index.md)  
[C# Anahtar Sözcükleri](index.md)  
[foreach, in](foreach-in.md)  
[for Deyimi (C++)](/cpp/cpp/for-statement-cpp)  
[Yineleme Deyimleri](iteration-statements.md)
