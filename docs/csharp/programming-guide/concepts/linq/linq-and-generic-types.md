---
title: LINQ ve Genel Türler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 02540db02d8e413ec254c0642d106ca41b263376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662523"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgu'nün 2.0 sürümünde tanıtılan genel türler dayanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Sorguları yazmaya başlamadan önce bir ayrıntılı bilgilere genel türler gerekmez. Ancak, iki temel kavramları anlamak isteyebilirsiniz:  
  
1.  Oluşturduğunuzda, bir genel koleksiyon sınıfının bir örneği gibi <xref:System.Collections.Generic.List%601>, "T" listenin tutulacağı nesne türüyle değiştirin. Örneğin, bir dize listesi olarak ifade edilir `List<string>`ve listesini `Customer` nesneleri olarak ifade edilir `List<Customer>`. Genel liste türü kesin olarak belirtilmiş ve öğeleri olarak depolayan koleksiyonlar üzerinden birçok avantaj sunar <xref:System.Object>. Eklemeyi denerseniz bir `Customer` için bir `List<string>`, derleme sırasında bir hata alırsınız. Çalışma zamanı tür atama gerçekleştirmek olmadığı için kullanımı kolay genel koleksiyonlar var.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> genel amaçlı koleksiyon sınıfları kullanarak numaralandırılmasını etkinleştirir arabirimi `foreach` deyimi. Genel koleksiyon sınıfları Destek <xref:System.Collections.Generic.IEnumerable%601> yalnızca gibi genel olmayan koleksiyon sınıfları gibi <xref:System.Collections.ArrayList> Destek <xref:System.Collections.IEnumerable>.  
  
 Genel türler hakkında daha fazla bilgi için bkz: [genel türler](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>IEnumerable < T\> LINQ sorgularında değişkenleri  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] olarak yazılan sorgu değişkenler <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir tür gibi <xref:System.Linq.IQueryable%601>. Olarak yazılmış bir sorgu değişkeni gördüğünüzde `IEnumerable<Customer>`, yalnızca sorgu yürütüldüğünde, bir dizi sıfır veya daha fazla üretecektir geldiğini `Customer` nesneleri.  
  
 [!code-csharp[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Daha fazla bilgi için [LINQ Sorgu işlemlerinde tür ilişkileri](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyici tanıtıcı genel tür bildirimleri izin vererek  
 İsterseniz, genel söz dizimini kullanarak kaçınabilirsiniz [var](../../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü. `var` Anahtar sözcüğü, belirtilen veri kaynağı bakarak bir sorgu değişkeni türünü çıkarsamak için derleyicinin bildirir `from` yan tümcesi. Aşağıdaki örnek önceki örnekle aynı derlenmiş kodunu üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 `var` Anahtar sözcüğü, ne zaman grubu sorgular tarafından üretilen kullananlar gibi iç içe geçmiş genel türleri açıkça belirtmek bu önemli değildir veya değişken türü belirgin olduğunda yararlıdır. Kullanırsanız, genel olarak, öneririz `var`, kodunuzu daha zor başkaları tarafından okunacak zorlaştırabilir emin farkında olun. Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Genel Türler](../../../../csharp/programming-guide/generics/index.md)
