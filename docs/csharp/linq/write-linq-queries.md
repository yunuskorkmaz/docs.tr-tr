---
title: C# içinde LINQ sorguları yazma
description: C# içinde LINQ sorguları yazma hakkında bilgi edinin.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 2ebba0d2d601932c976a88726fbe3ed37daffdcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559944"
---
# <a name="write-linq-queries-in-c"></a>C# içinde LINQ sorguları yazma #

Bu makalede, C# LINQ sorgusu yazma kullandığı üç yöntem açıklanır:

1. Sorgu söz dizimi kullanın.

2. Yöntem sözdizimini kullanın.

3. Sorgu sözdizimi ve yöntem sözdizimi bir birleşimini kullanın.

Aşağıdaki örnekler, daha önce listelenen her bir yaklaşım kullanarak bazı basit LINQ sorguları gösterir. Genel olarak, kullanım (1) mümkün olduğunda ve Kullan (2) ve (3) gerektiğinde kuralıdır.

> [!NOTE]
> Bu sorgular, basit bir bellek içi koleksiyonlarda çalışır; Ancak, temel sözdizimi, LINQ to Entities ve LINQ to XML kullanılıyor aynıdır.

## <a name="example---query-syntax"></a>Örnek - sorgu söz dizimi

Çoğu sorguları yazma için önerilen yöntem kullanmaktır *sorgu söz dizimi* oluşturmak için *sorgu ifadelerinde*. Aşağıdaki örnek, üç sorgu ifadeleri gösterir. İlk sorgu ifadesi filtreleyin veya koşullarla uygulayarak, sonuçları kısıtlama yapmayı gösteren bir `where` yan tümcesi. Değerleri 7 veya 3'ten az büyük olan kaynak dizisindeki tüm öğeleri döndürür. İkinci deyim, döndürülen sonuçların nasıl gösterir. Üçüncü ifade, sonuçları bir anahtar göre gruplandırmak gösterilmektedir. Bu sorgu, sözcüğün ilk harfini üzerinde alan iki gruplar döndürür.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Sorgu türü olduğuna dikkat edin <xref:System.Collections.Generic.IEnumerable%601>. Tüm bu sorguları kullanarak yazılabilir `var` aşağıdaki örnekte gösterildiği gibi:

`var query = from num in numbers...`

İçindeki sorgu değişkeni üzerinde yineleme kadar her önceki örnekte sorgular gerçekten Yürütülmeyen bir `foreach` deyimi veya diğer deyimi. Daha fazla bilgi için [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Örnek - yöntem sözdizimi

Bazı sorgu işlemlerinin bir yöntem çağrısının ifade edilmelidir. En yaygın tür yöntemler gibi tekil sayısal değerler döndüren olanlardır <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri. Yalnızca tek bir değeri temsil eder ve bir ek sorgu işlemi kaynağı olarak hizmet veremez bu yöntemlerin her zaman içinde herhangi bir sorgu son çağrılmalıdır. Aşağıdaki örnek bir sorgu ifadesinde yöntem çağrısı gösterir:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Yöntem bir eylem veya Func parametrelere sahipse, bunlar biçiminde sağlanır bir [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi ifade:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

Önceki sorgular, yalnızca sorgu #4 hemen yürütür. Tek bir değer ve bir genel döndürür olmasıdır <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu. Yöntemin kendisi kullanması gereken `foreach` değerini hesaplamak için.

Her biri, önceki sorgular ile örtülü yazma'yı kullanarak yazılabilir [var](../language-reference/keywords/var.md), aşağıdaki örnekte gösterildiği gibi:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Örnek - karma sorgu ve yöntem sözdizimi

Bu örnek, bir sorgu yan tümcesinin sonuçlarını temel yöntem sözdizimi kullanmayı gösterir. Yalnızca sorgu ifadesi, parantez içine ve ardından nokta işleci uygulamak ve yöntemi çağırın. Aşağıdaki örnekte, sorgu #7, 3 ve 7 arasında bir değeri olan sayıların sayısını döndürür. Genel olarak, ancak bu ikinci bir değişkene yöntem çağrısının sonucunu depolamak için kullanmak en iyisidir. Bu şekilde, sorgu sorgu sonuçlarını kafanız olma olasılığı daha gereklidir.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Sorgu, sorgu #7 tek bir değer ve bir koleksiyonu döndürdüğünden, hemen yürütür.

Önceki sorguya ile örtülü yazma'yı kullanarak yazılabilir `var`gibi:

```csharp
var numCount = (from num in numbers...
```

Bunu şu şekilde yöntemi sözdiziminde yazılabilir:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Açık, şu şekilde yazım kullanarak yazılabilir:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Sorgu C# dilinde yazma](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [where yan tümcesi](../language-reference/keywords/where-clause.md)