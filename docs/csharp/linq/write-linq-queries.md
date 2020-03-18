---
title: C# içinde LINQ sorguları yazma
description: C#'da LINQ sorguları nasıl yazılanın öğrenin.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632885"
---
# <a name="write-linq-queries-in-c"></a>C'ye LINQ sorguları yazın\#

Bu makalede, C#'da bir LINQ sorgusu yazabileceğiniz üç yol gösterilmektedir:

1. Sorgu sözdizimini kullanın.

2. Yöntem sözdizimini kullanın.

3. Sorgu sözdizimi ve yöntem sözdizimi nin bir birleşimini kullanın.

Aşağıdaki örnekler, daha önce listelenen her yaklaşımı kullanarak bazı basit LINQ sorgularını gösterir. Genel olarak, kural (1) mümkün olduğunca kullanmak ve (2) ve (3) gerektiğinde kullanmaktır.

> [!NOTE]
> Bu sorgular basit bellek içi koleksiyonlarda çalışır; ancak, temel sözdizimi Linq'de Kullanılanvarlıklarla ve LINQ'dan XML'e aynıdır.

## <a name="example---query-syntax"></a>Örnek - Sözdizimini sorgula

Çoğu sorgu yazmanın önerilen yolu sorgu *ifadeleri*oluşturmak için *sorgu sözdizimini* kullanmaktır. Aşağıdaki örnekte üç sorgu ifadesi gösterilmektedir. İlk sorgu ifadesi, bir `where` yan tümceyle koşullar uygulayarak sonuçların nasıl filtrelenebildiğini veya kısıtlanın. Değerleri 7'den büyük veya 3'ten küçük olan kaynak dizisindeki tüm öğeleri döndürür. İkinci ifade, döndürülen sonuçların nasıl sıralanın gösterildiğini gösterir. Üçüncü ifade, sonuçların bir anahtara göre nasıl gruplatını gösterir. Bu sorgu, sözcüğün ilk harfini temel alan iki grubu döndürür.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Sorguların türü . <xref:System.Collections.Generic.IEnumerable%601> Tüm bu sorgular aşağıdaki `var` örnekte gösterildiği gibi kullanılarak yazılabilir:

`var query = from num in numbers...`

Önceki her örnekte, bir deyimveya başka bir `foreach` deyimdeki sorgu değişkeni üzerinde yinelene kadar sorgular gerçekten yürütülmez. Daha fazla bilgi için [LINQ Sorgularına Giriş'e](../programming-guide/concepts/linq/introduction-to-linq-queries.md)bakın.

## <a name="example---method-syntax"></a>Örnek - Yöntem sözdizimi

Bazı sorgu işlemleri bir yöntem çağrısı olarak ifade edilmelidir. En yaygın bu tür yöntemler, singleton sayısal değerleri <xref:System.Linq.Enumerable.Sum%2A>döndüren yöntemlerdir, , , <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A>, ve benzeri. Bu yöntemler, yalnızca tek bir değeri temsil ettikleri ve ek bir sorgu işlemi için kaynak olarak hizmet veremedikleri nden, her zaman herhangi bir sorguda sonuncu olarak adlandırılmalıdır. Aşağıdaki örnekte sorgu ifadesinde bir yöntem çağrısı gösterilmektedir:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Yöntemde Action veya Func parametreleri varsa, bunlar aşağıdaki örnekte gösterildiği gibi [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) ifadesi biçiminde sağlanır:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

Önceki sorgularda, yalnızca Sorgu #4 hemen yürütülür. Bunun nedeni, genel <xref:System.Collections.Generic.IEnumerable%601> bir koleksiyon değil, tek bir değer döndürmesidir. Yöntemin değerini hesaplamak için kendisi kullanmak `foreach` zorundadır.

Önceki sorguların her biri aşağıdaki örnekte gösterildiği [gibi, var](../language-reference/keywords/var.md)ile örtük yazarak yazılabilir:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Örnek - Karma sorgu ve yöntem sözdizimi

Bu örnek, bir sorgu yan tümcesinin sonuçlarında yöntem sözdiziminin nasıl kullanılacağını gösterir. Sorgu ifadesini parantez içine eklemeniz ve nokta işlecini uygulayın ve yöntemi arayın. Aşağıdaki örnekte, sorgu #7 değeri 3 ile 7 arasında olan sayıların sayısını döndürür. Genel olarak, ancak, yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak daha iyidir. Bu şekilde, sorgunun sorgu sonuçlarıyla karıştırılma olasılığı daha düşüktür.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Sorgu #7 bir koleksiyon değil, tek bir değer döndürdüğünden, sorgu hemen yürütülür.

Önceki sorgu, aşağıdaki gibi örtülü `var`yazarak yazılabilir:

```csharp
var numCount = (from num in numbers...
```

Yöntem sözdiziminde aşağıdaki gibi yazılabilir:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Aşağıdaki gibi, açık yazarak yazılabilir:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: C'de Sorgu Yazma #](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [where tümcesi](../language-reference/keywords/where-clause.md)
