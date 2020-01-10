---
title: yield bağlamsal anahtar sözcük C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712786"
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)

Bir ifadede `yield` [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, göründüğü yöntemin, işlecin veya `get` erişimcisinin bir yineleyici olduğunu belirtirsiniz. Bir yineleyici tanımlamak için `yield` kullanmak, özel bir koleksiyon türü için <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> modelini uyguladığınızda, açık bir ek sınıfa yönelik gereksinimi ortadan kaldırır (bir numaralandırma için durumu tutan sınıf, bir örnek için bkz. <xref:System.Collections.Generic.IEnumerator%601>).

Aşağıdaki örnek `yield` deyimin iki biçimini gösterir.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Açıklamalar

Her bir öğeyi birer birer döndürmek için bir `yield return` ifadesini kullanın.

Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir. `foreach` döngüsünün her yinelemesi yineleyici yöntemini çağırır. Yineleyici yönteminde bir `yield return` ifadesine ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.

Yinelemeyi sonlandırmak için `yield break` bir ifade kullanabilirsiniz.

Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Yineleyici yöntemleri ve get erişimcileri

Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:

- Dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olmalıdır.

- Bildirimin [parametreleri olamaz](in-parameter-modifier.md) [ref](ref.md) veya [Out](out-parameter-modifier.md) .

<xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> döndüren bir yineleyicinin `yield` türü `object`.  Yineleyici <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>döndürürse, `yield return` deyimindeki ifadenin türünden genel tür parametresine örtük bir dönüştürme olmalıdır.

İçine bir `yield return` veya `yield break` ifadesini ekleyemezsiniz:

- [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).

- Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).

## <a name="exception-handling"></a>Özel durum işleme

Bir `yield return` deyimleri, try-catch bloğunda bulunamaz. Bir `yield return` deyimleri, try-finally ifadesinin try bloğunda bulunabilir.

`yield break` bir ifade, bir try bloğunda veya catch bloğunda bulunabilir ancak finally bloğunda yer alabilir.

`foreach` gövdesi (yineleyici yöntemi dışında) bir özel durum oluşturursa, yineleyici yönteminde bir `finally` bloğu yürütülür.

## <a name="technical-implementation"></a>Teknik uygulama

Aşağıdaki kod bir yineleyici yönteminden bir `IEnumerable<string>` döndürür ve sonra öğeleri boyunca yinelenir.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

`MyIteratorMethod` çağrısı, yönteminin gövdesini yürütmez. Bunun yerine, çağrı `elements` değişkenine bir `IEnumerable<string>` döndürür.

`foreach` döngüsünün bir yinelemesi üzerinde `elements`için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi çağırılır. Bu çağrı, sonraki `yield return` ifadesine ulaşılana kadar `MyIteratorMethod` gövdesini yürütür. `yield return` deyiminin döndürdüğü ifade, yalnızca döngü gövdesine göre tüketim için `element` değişkeninin değerini değil, bir `IEnumerable<string>`olan `elements`<xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliğini de belirler.

`foreach` döngüsünün sonraki tekrarında, yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir `yield return` bildirimine ulaştığında yeniden durdurulur. Yineleyici yönteminin sonuna veya bir `yield break` ifadesine ulaşıldığında `foreach` döngüsü tamamlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `for` döngüsünün içindeki bir `yield return` bildirimine sahiptir. `Main` yönteminde `foreach` bildiri gövdesinin her yinelemesi `Power` Yineleyici işlevine bir çağrı oluşturur. Yineleyici işlevine yapılan her çağrı, `for` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `yield return` deyimin bir sonraki yürütmeye ilerler.

Yineleyici yönteminin dönüş türü, bir Yineleyici arabirimi türü olan <xref:System.Collections.IEnumerable>. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, yineleyici olan bir `get` erişimcisini gösterir. Örnekte, her `yield return` ekstresi Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Yineleyiciler](../../iterators.md)
