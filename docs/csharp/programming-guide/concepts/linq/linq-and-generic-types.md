---
title: LINQ ve Genel Türler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: f9bb4ec21685d21d0975529c7460944b5f0f9fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327743"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, 2.0 sürümünde tanıtılan genel türler temel [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Sorgu yazma başlamadan önce bilgisi genel türler derinlemesine gerekmez. Ancak, iki temel kavramlarını anladığınızdan isteyebilirsiniz:  
  
1.  Oluştururken bir genel koleksiyon sınıfının bir örneği gibi <xref:System.Collections.Generic.List%601>, "T" listesi tutacak nesnelerin türünü değiştirin. Örneğin, dizelerinin listesini olarak ifade edilir `List<string>`ve listesini `Customer` nesneleri olarak ifade edilir `List<Customer>`. Genel listesini kesin türü belirtilmiş ve kendi öğeleri olarak depolamak koleksiyonlar üzerinden birçok avantaj sunar <xref:System.Object>. Eklemeyi denediğinizde bir `Customer` için bir `List<string>`, derleme zamanı sırasında bir hata iletisi alır. Çalışma zamanı tür-atama gerçekleştirmek olmadığı için kullanımı kolay genel koleksiyonlar var.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> arabirimi kullanarak sıralanması genel koleksiyon sınıfları sağlar `foreach` deyimi. Genel koleksiyon sınıfları Destek <xref:System.Collections.Generic.IEnumerable%601> yalnızca olarak genel olmayan koleksiyonu sınıfları gibi <xref:System.Collections.ArrayList> Destek <xref:System.Collections.IEnumerable>.  
  
 Genel türler hakkında daha fazla bilgi için bkz: [genel türler](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>IEnumerable < T\> LINQ sorgularını değişkenleri  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu değişkenleri olarak yazılan <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir tür gibi <xref:System.Linq.IQueryable%601>. Olarak yazılan bir sorgu değişkeni gördüğünüzde `IEnumerable<Customer>`, yalnızca yürütüldüğünde, sorgu, sıfır veya daha fazla dizisini üretecektir gelir `Customer` nesneleri.  
  
 [!code-csharp[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Daha fazla bilgi için bkz: [LINQ Sorgu işlemlerinde tür ilişkileri](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyici tanıtıcı genel tür bildirimleri izin vererek  
 İsterseniz, kullanarak genel sözdizimi önleyebilirsiniz [var](../../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü. `var` Anahtar sözcüğü bir sorgu değişkeninin türü belirtilen veri kaynağı bakarak gerçekleştirip derleyici bildirir `from` yan tümcesi. Aşağıdaki örnek önceki örnekteki gibi aynı derlenmiş kod üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 `var` Anahtar sözcüğü, değişkenin türü açık olduğunda veya ne zaman Grup sorgular tarafından üretilen olanlar gibi iç içe geçmiş genel türler açıkça belirtmek bu önemli değildir yararlıdır. Kullanırsanız, genel olarak, öneririz `var`, kodunuzu daha başkalarının okunmasını zorlaştırabilir olduğunu unutmayın. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Genel Türler](../../../../csharp/programming-guide/generics/index.md)
