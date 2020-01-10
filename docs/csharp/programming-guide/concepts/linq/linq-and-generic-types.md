---
title: LINQ ve Genel Türler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 9a2d1ac72f70e7cd314d349e81ab2bc815a5bf13
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635580"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
LINQ sorguları, .NET Framework sürüm 2,0 ' de tanıtılan genel türleri temel alır. Sorgu yazmaya başlayabilmeniz için önce genel türler hakkında ayrıntılı bilgi sahibi olmanız gerekmez. Ancak, iki temel kavramı anlamak isteyebilirsiniz:  
  
1. <xref:System.Collections.Generic.List%601>gibi bir genel koleksiyon sınıfının bir örneğini oluşturduğunuzda, "T" öğesini listenin tutacaksınız nesne türüyle değiştirirsiniz. Örneğin, dizelerin bir listesi `List<string>`olarak ifade edilir ve `Customer` nesnelerinin bir listesi `List<Customer>`olarak ifade edilir. Genel liste kesin bir şekilde yazılır ve öğelerini <xref:System.Object>olarak depolayan koleksiyonlar üzerinde birçok avantaj sağlar. Bir `List<string>``Customer` eklemeye çalışırsanız, derleme zamanında bir hata alırsınız. Çalışma zamanı türü atama gerçekleştirmeniz zorunda olmadığınızdan genel koleksiyonları kullanmak kolaydır.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>, genel koleksiyon sınıflarının `foreach` deyimleri kullanılarak numaralandırılmasını sağlayan arabirimdir. Genel koleksiyon sınıfları, <xref:System.Collections.ArrayList> desteği <xref:System.Collections.IEnumerable>gibi genel olmayan koleksiyon sınıfları gibi <xref:System.Collections.Generic.IEnumerable%601> destekler.  
  
 Genel türler hakkında daha fazla bilgi için bkz. [Genel türler](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>LINQ sorgularında IEnumerable < T\> değişkenleri  
 LINQ sorgu değişkenleri <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>gibi türetilmiş bir tür olarak yazılır. `IEnumerable<Customer>`olarak yazılan bir sorgu değişkeni gördüğünüzde, sorgu yürütüldüğü zaman sorgunun sıfır veya daha fazla `Customer` nesne sırası üretebileceği anlamına gelir.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyicinin genel tür bildirimleri tanıtıcısına izin verme  
 Tercih ederseniz, [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak genel sözdiziminden kaçınabilirsiniz. `var` anahtar sözcüğü, derleyiciye `from` yan tümcesinde belirtilen veri kaynağına bakarak bir sorgu değişkeninin türünü çıkarmasını söyler. Aşağıdaki örnek, önceki örnekle aynı derlenmiş kodu üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var` anahtar sözcüğü, değişkenin türü açık olduğunda veya grup sorguları tarafından üretilenler gibi iç içe geçmiş genel türleri açıkça belirtmek önemli olmadığında yararlıdır. Genel olarak, `var`kullanıyorsanız, kodunuzun başkalarının okuması için daha zor hale yapabileceğini fark etmiş olursunuz. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](../../generics/index.md)
