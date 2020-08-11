---
title: C# içinde LINQ sorguları yazma
description: C# dilinde LINQ sorguları yazmayı öğrenin.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: bd7da81f2873c6a25570cab32fafecc66fd98be4
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063451"
---
# <a name="write-linq-queries-in-c"></a>C 'de LINQ sorguları yazma\#

Bu makalede C# dilinde LINQ sorgusu yazabileceğiniz üç yol gösterilmektedir:

1. Sorgu söz dizimini kullanın.

2. Yöntem sözdizimini kullanın.

3. Sorgu söz dizimi ve Yöntem sözdizimi birleşimini kullanın.

Aşağıdaki örneklerde, daha önce listelenen her yaklaşımı kullanarak bazı basit LINQ sorguları gösterilmektedir. Genel olarak, kural mümkün olduğunca (1) kullanılır ve gerektiğinde (2) ve (3) kullanır.

> [!NOTE]
> Bu sorgular, basit bellek içi koleksiyonlar üzerinde çalışır; Ancak, temel sözdizimi LINQ to Entities ve LINQ to XML ' de kullanılan ile aynıdır.

## <a name="example---query-syntax"></a>Örnek-sorgu söz dizimi

Çoğu sorgu yazmak için önerilen yol sorgu *ifadelerini*oluşturmak için *sorgu sözdizimini* kullanmaktır. Aşağıdaki örnek, üç sorgu ifadesini gösterir. İlk sorgu ifadesi, bir yan tümcesiyle koşulları uygulayarak sonuçların nasıl filtreleneceğini veya kısıtlanacağını gösterir `where` . Kaynak dizisindeki, değerleri 7 ' den büyük veya 3 ' ten küçük olan tüm öğeleri döndürür. İkinci ifade, döndürülen sonuçların nasıl sıraya alınacağını gösterir. Üçüncü ifade, sonuçların bir anahtara göre nasıl gruplandırılacağını gösterir. Bu sorgu, sözcüğün ilk harfine göre iki grup döndürür.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Sorguların türünün olduğunu unutmayın <xref:System.Collections.Generic.IEnumerable%601> . Bu sorguların hepsi `var` , aşağıdaki örnekte gösterildiği gibi kullanılarak yazılabilir:

`var query = from num in numbers...`

Bir önceki örnekte, sorgu değişkeni üzerinde veya başka bir bildirimde yineleme yapana kadar sorgular aslında yürütülmez `foreach` . Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Örnek yöntem sözdizimi

Bazı sorgu işlemleri bir yöntem çağrısı olarak ifade edilmesi gerekir. En sık kullanılan yöntemler,,,, vb. gibi tekil sayısal değerler döndüren <xref:System.Linq.Enumerable.Sum%2A> olanlardır <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A> . Yalnızca tek bir değeri temsil ettiğinden ve ek bir sorgu işlemi için kaynak olarak işlev veremediği için, bu yöntemlerin her zaman herhangi bir sorguda en son çağrılması gerekir. Aşağıdaki örnek bir sorgu ifadesinde bir yöntem çağrısını gösterir:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Yöntemin Action veya Func parametreleri varsa, bunlar aşağıdaki örnekte gösterildiği gibi bir [lambda](../language-reference/operators/lambda-expressions.md) ifadesi biçiminde sağlanır:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

Önceki sorgularda yalnızca Query #4 hemen yürütülür. Bunun nedeni, genel bir koleksiyon değil tek bir değer döndürmektedir <xref:System.Collections.Generic.IEnumerable%601> . Metodun kendi `foreach` değerini hesaplamak için kullanması gerekmez.

Önceki sorguların her biri, aşağıdaki örnekte gösterildiği gibi, [var](../language-reference/keywords/var.md)ile örtük yazma kullanılarak yazılabilir:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Örnek-karışık sorgu ve Yöntem sözdizimi

Bu örnek, bir sorgu yan tümcesinin sonuçlarında Yöntem sözdiziminin nasıl kullanılacağını gösterir. Sorgu ifadesini parantez içine almalısınız ve sonra nokta işlecini uygulayıp yöntemi çağırın. Aşağıdaki örnekte, Query #7 değeri 3 ile 7 arasında olan sayıların sayımını döndürür. Ancak genel olarak, yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak daha iyidir. Bu şekilde sorgunun sonuçlarıyla karışması daha düşüktür.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Sorgu #7 bir koleksiyon değil tek bir değer döndürdüğünden sorgu hemen yürütülür.

Önceki sorgu, aşağıdaki gibi örtük yazma kullanılarak yazılabilir `var` :

```csharp
var numCount = (from num in numbers...
```

Yöntem sözdiziminde aşağıdaki gibi yazılabilir:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Açık yazma kullanılarak şu şekilde yazılabilir:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: C 'de sorgu yazma #](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [where tümcesi](../language-reference/keywords/where-clause.md)
