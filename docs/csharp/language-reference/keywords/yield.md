---
description: yield bağlamsal anahtar sözcüğü-C# başvurusu
title: yield bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e0efad959d5212f6c07d4c4b5344761490018a4c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899671"
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)

`yield`Bir ifadede [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, görünen yöntemin, işlecin veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz. Bir `yield` Yineleyici tanımlamak için kullanmak, <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> özel bir koleksiyon türü için ve modelini uyguladığınızda açık bir ek sınıfa (bir sabit listesinin durumunu tutan sınıf için bkz. bir örnek için bkz.) gereksinimi ortadan kaldırır <xref:System.Collections.IEnumerator> .

Aşağıdaki örnekte, ifadesinin iki formu gösterilmektedir `yield` .

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Açıklamalar

`yield return`Her öğeyi birer birer döndürmek için bir ifade kullanırsınız.

Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir. Döngünün her yinelemesi `foreach` yineleyici yöntemini çağırır. `yield return`Yineleyici yönteminde bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.

`yield break`Yinelemeyi sonlandırmak için bir ifade kullanabilirsiniz.

Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Yineleyici yöntemleri ve get erişimcileri

Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:

- Dönüş türü <xref:System.Collections.IEnumerable> ,, veya olmalıdır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .

- Bildirimde hiç [ın](in-parameter-modifier.md), [ref](ref.md)veya [Out](out-parameter-modifier.md) parametresi olamaz.

`yield`Veya döndüren bir yineleyici türü <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> `object` .  Yineleyici <xref:System.Collections.Generic.IEnumerable%601> veya döndürürse, deyimde <xref:System.Collections.Generic.IEnumerator%601> deyim türünden genel tür parametresine örtük bir dönüştürme olmalıdır `yield return` .

`yield return` `yield break` İçine or ifadesini ekleyemezsiniz:

- [Lambda ifadeleri](../operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).

- Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).

## <a name="exception-handling"></a>Özel durum işleme

Bir `yield return` ifade, try-catch bloğunda bulunamaz. Bir `yield return` ifade, try-finally ifadesinin try bloğunda bulunabilir.

Bir `yield break` ifade bir try bloğunda veya catch bloğunda bulunabilir, ancak finally bloğunda yer alabilir.

`foreach`Gövde (yineleyici yönteminin dışında) bir özel durum oluşturursa, `finally` yineleyici yönteminde bir blok yürütülür.

## <a name="technical-implementation"></a>Teknik uygulama

Aşağıdaki kod bir `IEnumerable<string>` Yineleyici yönteminden bir döndürür ve sonra öğeleri boyunca yinelenir.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Çağrısı, `MyIteratorMethod` yönteminin gövdesini yürütmez. Bunun yerine, çağrı `IEnumerable<string>` değişkenine bir döndürür `elements` .

Döngüsünün bir yinelemesinde `foreach` , <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements` . Bu çağrı, `MyIteratorMethod` sonraki `yield return` ifadeye ulaşılana kadar gövdesini yürütür. Deyimi tarafından döndürülen ifade, `yield return` yalnızca `element` döngü gövdesi tarafından tüketim için değişkenin değerini değil <xref:System.Collections.Generic.IEnumerator%601.Current%2A> , öğesinin özelliğini de bir olarak belirler `elements` `IEnumerable<string>` .

Döngünün sonraki tekrarında `foreach` , yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `yield return` . `foreach`Yineleyici yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `yield return` döngüsünün içinde olan bir ifade vardır `for` . `foreach`Yöntemi içindeki ifade gövdesinin her yinelemesi, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` . Yineleyici işlevine yapılan her çağrı, `yield return` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `for` .

Yineleyici yönteminin dönüş türü <xref:System.Collections.IEnumerable> , yineleyici arabirim türü olan. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `get` Yineleyici olan bir erişimciyi gösterir. Örnekte, her bir `yield return` ifade Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Yineleyiciler](../../iterators.md)
