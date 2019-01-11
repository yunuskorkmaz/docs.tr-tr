---
title: bağlamsal anahtar sözcük - yield C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: cfeef1d84a443163f4bbeda863682335d9cd1fcd
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222630"
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)

Kullandığınızda `yield` [bağlamsal anahtar sözcük](index.md#contextual-keywords) bir deyimde, belirttiğiniz yöntemin, işlecin veya `get` erişimci görünür olan bir yineleyici. Kullanarak `yield` bir yineleyici tanımlamak için açık bir ekstra sınıf gereksinimini ortadan kaldırır (bir numaralandırma için durumu tutan sınıf, bkz <xref:System.Collections.Generic.IEnumerator%601> örneği) uyguladığınızda <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> özel bir koleksiyona deseni yazın.

Aşağıdaki örnek, iki formunu gösterir `yield` deyimi.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Açıklamalar

Kullandığınız bir `yield return` her öğeyi bir defada döndürmek için deyimi.

Kullanarak bir yineleyici yöntemini kullanan bir [foreach](foreach-in.md) deyimini veya LINQ sorgusunu. Her bir yinelemesini `foreach` döngüsü yineleyici yöntemini çağırır. Olduğunda bir `yield return` yineleyici yöntem içinde deyimine ulaşıldığında `expression` döndürülür ve kodun geçerli konumu korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.

Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.

Yineleyiciler hakkında daha fazla bilgi için bkz: [yineleyiciler](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Yineleyici yöntemleri ve get erişimcileri

Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:

- Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.

- Bildirimi içeremez [içinde](in-parameter-modifier.md) [ref](ref.md) veya [kullanıma](out-parameter-modifier.md) parametreleri.

`yield` Türü döndüren bir yineleyicinin <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> olduğu `object`.  Yineleyici döndürürse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>, ifadesinde türü örtük bir dönüştürme olmalıdır `yield return` genel tür parametresine deyimi.

Dahil edemezsiniz bir `yield return` veya `yield break` aşağıdaki özelliklere sahip yöntemlerini deyiminin:

- Anonim yöntemler. Daha fazla bilgi için [anonim yöntemler](../../programming-guide/statements-expressions-operators/anonymous-methods.md).

- Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için [güvenli](unsafe.md).

## <a name="exception-handling"></a>Özel durum işleme

A `yield return` ifadesi bir try-catch bloğu içinde bulunamaz. A `yield return` ifadesi bir try-finally ifadesinin try bloğunda bulunabilir.

A `yield break` ifadesi bir try bloğu ya da bir catch bloğu içinde bulunabilir ama bir finally bloğunda.

Varsa `foreach` gövdesi (yineleyici yöntemi dışında) bir özel durum oluşturursa bir `finally` yineleyici yöntem bloğunda yürütülür.

## <a name="technical-implementation"></a>Teknik uygulama

Aşağıdaki kod döndürür bir `IEnumerable<string>` yineleyici yöntemden ve sonra öğeleri boyunca yinelenir.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Çağrı `MyIteratorMethod` yöntemin gövdesini yürütmez. Bunun yerine çağrı döndürür bir `IEnumerable<string>` içine `elements` değişkeni.

Yinelemesi üzerinde `foreach` döngü <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`. Bu çağrı gövdesini yürütür `MyIteratorMethod` sonraki kadar `yield return` deyimine ulaşıldığında. Tarafından döndürülen ifade `yield return` deyimi yalnızca değerini belirler `element` döngü gövdesinin tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliği `elements`, olduğu bir `IEnumerable<string>`.

Her yinelemesinde `foreach` kadar yineleyici gövdenin yürütülmesi devam eder, döngü onu ulaştığında yeniden kaldığı bir `yield return` deyimi. `foreach` Tamamlandıktan döngüsü yineleyici yöntemin sonuna ya da bir `yield break` deyimine ulaşıldığında.

## <a name="example"></a>Örnek

Aşağıdaki örnek sahip bir `yield return` içindeki bir `for` döngü. Her bir yinelemesini `foreach` deyiminin gövdesinde `Main` yöntemine bir çağrı oluşturur `Power` yineleyici işlevi. Her yineleyici işleve çağrı için sonraki yürütme devam eder `yield return` sıradaki yinelemesi süresince gerçekleşen deyimi `for` döngü.

Yineleyici yöntemin dönüş türü <xref:System.Collections.IEnumerable>, bir yineleyici arabirimi türü. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, gösterir bir `get` bir yineleyici erişimcisi. Örnekte, her `yield return` deyimi, kullanıcı tanımlı bir sınıfın bir örneği döndürür.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Yineleyiciler](../../iterators.md)