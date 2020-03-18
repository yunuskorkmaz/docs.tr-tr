---
title: içeriksel anahtar kelime verim - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712786"
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)

Bir deyimde `yield` [bağlamsal anahtar kelimeyi](index.md#contextual-keywords) kullandığınızda, görüntülendiği yöntemin, işleç veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz. Bir `yield` yineleyici tanımlamak için kullanmak, özel bir koleksiyon türü için <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> deseni uyguladığınız zaman açık bir ek sınıf (numaralandırma için durumu tutan sınıf, örneğine bakın) gereksinimini ortadan kaldırır.

Aşağıdaki örnek, `yield` deyimin iki biçimini gösterir.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Açıklamalar

Her öğeyi birer birer döndürmek için bir `yield return` deyim kullanırsınız.

Bir yineleyici yönteminden döndürülen [sıra, foreach](foreach-in.md) deyimi veya LINQ sorgusu kullanılarak tüketilebilir. Döngünün `foreach` her yinelemesi yineleyici yöntemini çağırır. Yineleyici `yield return` yönteminde bir deyime ulaşıldığında `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.

Yinelemeyi sona `yield break` erdirmek için bir deyim kullanabilirsiniz.

Yineleyiciler hakkında daha fazla bilgi için [bkz.](../../iterators.md)

## <a name="iterator-methods-and-get-accessors"></a>Yineleyici yöntemleri ve erişime erişim

Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:

- İade türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>veya .

- Beyannamede [hakem](ref.md) veya [çıkış](out-parameter-modifier.md) [parametreleri](in-parameter-modifier.md) olamaz.

Döndüren `yield` <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> döndüren `object`bir yineleyici türü.  Yineleyici dönerse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>deyimdeki `yield return` ifade türünden genel tür parametresine örtülü bir dönüştürme olması gerekir.

Şuna bir `yield return` ekstre veya `yield break` deyim ekemezsiniz:

- [Lambda ifadeler](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [anonim yöntemler](../operators/delegate-operator.md).

- Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için [güvenli olmayan.](unsafe.md)

## <a name="exception-handling"></a>Özel durum işleme

Bir `yield return` deyim try-catch bloğunda bulunamaz. Bir `yield return` deyim, try-finally deyiminin try bloğunda bulunabilir.

Bir `yield break` deyim bir try bloğunda veya yakalama bloğunda bulunabilir, ancak son bir blokta bulunamaz.

`foreach` Gövde (yineleyici yöntemi nin dışında) bir özel durum `finally` atarsa, yineleyici yönteminde bir blok çalıştırılır.

## <a name="technical-implementation"></a>Teknik uygulama

Aşağıdaki kod bir `IEnumerable<string>` yineleyici yönteminden bir döndürür ve sonra öğeleri ile yineleme.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Çağrı, `MyIteratorMethod` yöntemin gövdesini yürütmez. Bunun yerine çağrı `IEnumerable<string>` `elements` değişkene bir döndürür.

`foreach` Döngü bir yineleme üzerinde, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntem için `elements`çağrılır. Bu çağrı, bir `MyIteratorMethod` sonraki `yield return` ifadeye ulaşılına kadar gövdeyi yürütür. `yield return` İfade tarafından döndürülen ifade, yalnızca döngü `element` gövdesi tarafından tüketim için değişkenin <xref:System.Collections.Generic.IEnumerator%601.Current%2A> değerini `elements`değil, `IEnumerable<string>`aynı zamanda bir .

Döngünün `foreach` sonraki her yinelemesinde, yineleme gövdesinin yürütülmesi kaldığı yerden devam ediyor ve bir `yield return` ifadeye ulaştığında yine durur. Yineleme `foreach` yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `yield return` bir `for` döngü içinde bir deyim vardır. Yöntemde ifade gövdesinin `foreach` `Main` her yineleme `Power` yineleyici işlevine bir çağrı oluşturur. Yineleyici işlevine yapılan her çağrı, `yield return` `for` döngünün bir sonraki yinelemesi sırasında oluşan deyimin bir sonraki yürütmesine ilerler.

Yineleyici yönteminin dönüş <xref:System.Collections.IEnumerable>türü, bir yineleyici arabirim türüdür. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `get` yineleyici olan bir erişimci gösterir. Örnekte, her `yield return` deyim kullanıcı tanımlı bir sınıfın bir örneğini döndürür.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Yineleyiciler](../../iterators.md)
