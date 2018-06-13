---
title: C# içinde LINQ sorguları yazma
description: Nasıl yazılacağını sorgular.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288843"
---
# <a name="write-linq-queries-in-c"></a>C# içinde LINQ sorguları yazma

Bu konu, C# üzerinde LINQ sorgu yazabilirsiniz üç şekilde gösterir:  
  
1.  Sorgu sözdizimini kullanın.  
  
2.  Yöntemi sözdizimini kullanın.  
  
3.  Sorgu sözdizimi ve yöntem sözdizimi bileşimini kullanın.  
  
 Aşağıdaki örnekler, daha önce listelenen her bir yaklaşım kullanarak bazı basit LINQ sorgularını gösterir. Genel olarak, kullanım (1) mümkün olduğunda ve Kullan (2) ve (3) gerektiğinde kuralıdır.  
  
> [!NOTE]
>  Bu sorguları basit bellek içi koleksiyonlar üzerinde çalışır; Ancak, temel sözdizimi LINQ to Entities ve LINQ-XML kullanılan aynıdır.  
  
## <a name="example"></a>Örnek  
  
## <a name="query-syntax"></a>Sorgu sözdizimi  
 Sorguların çoğu yazmak için önerilen yöntem kullanmaktır *sorgu sözdizimi* oluşturmak için *sorgu ifadeleri*. Aşağıdaki örnekte, üç sorgu ifadeleri gösterir. Filtre veya koşullar uygulayarak sonuçları kısıtlamak nasıl ilk sorgu ifadesi gösteren bir `where` yan tümcesi. Değerleri 7 veya 3'ten az büyük olan kaynak dizisindeki tüm öğeleri döndürür. İkinci ifade döndürülen sonuçların sipariş gösterilmiştir. Üçüncü ifade, sonuçları bir anahtar göre gruplandırmak gösterilmiştir. Bu sorgu sözcüğün ilk harfini göre iki grupları döndürür.  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 Sorguları türünde Not <xref:System.Collections.Generic.IEnumerable%601>. Tüm bu sorguları kullanarak yazılabilir `var` aşağıdaki örnekte gösterildiği gibi:  
  
 `var query = from num in numbers...`  
  
 Sorgu değişkeninde üzerinden yineleme kadar her önceki örnekte sorguları gerçekte yürütmeme bir `foreach` deyimi veya diğer deyimi. Daha fazla bilgi için bkz: [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="example"></a>Örnek  
  
## <a name="method-syntax"></a>Yöntem sözdizimi  
 Bazı sorgu işlemleri bir yöntem çağrısı ifade edilmesi gerekir. En yaygın tür yöntem dönüş singleton sayısal değerleri gibi izinlerdir <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri. Yalnızca tek bir değeri temsil eder ve bir ek sorgu işlemi için kaynak olarak sunulamıyor olduğundan bu yöntemlerin her zaman içinde herhangi bir sorgu son çağrılmalıdır. Aşağıdaki örnek, sorgu ifadesinde bir yöntem çağrısı gösterir:  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a>Örnek  
 Yöntem bir eylem veya Func parametrelere sahipse, bunlar biçiminde sağlanan bir [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi ifade:  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 Önceki sorgularında yalnızca sorgu #4 hemen yürütür. Tek bir değer ve bir genel döndürür olmasıdır <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu. Yöntemin kendisi kullanması gereken `foreach` değerini hesaplamak üzere.  
  
 Her bir önceki sorgu ile örtük yazarak kullanarak yazılabilir [var](../language-reference/keywords/var.md), aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a>Örnek  
  
## <a name="mixed-query-and-method-syntax"></a>Karma sorgu ve yöntem sözdizimi  
 Bu örnek bir sorgu yan tümcesinin sonuçlarını temel yöntem sözdizimi kullanmayı gösterir. Yalnızca sorgu ifadesi parantez içine alın ve ardından nokta işleci uygulamak ve yöntemini çağırın. Aşağıdaki örnekte, sorgu #7 değeri 3 ile 7 arasında olan sayıları sayısını döndürür. Genel olarak, ancak bu yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak en iyisidir. Bu şekilde, sorgu sorgu sonuçlarını kafası olması daha az olasıdır.  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 Sorgu #7 tek bir değer ve bir koleksiyon döndürdüğünden, sorguyu hemen yürütür.  
  
 Önceki sorgu ile örtük yazarak kullanarak yazılabilir `var`aşağıdaki gibi:  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 Bunu şu şekilde yöntemi sözdiziminde yazılabilir:  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 Açık, aşağıdaki gibi yazarak kullanarak yazılabilir:  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
  [İzlenecek yol: Sorguları C# ile yazma](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [LINQ Sorgu ifadeleri](index.md)  
 [where yan tümcesi](../language-reference/keywords/where-clause.md)
