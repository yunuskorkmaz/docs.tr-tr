---
title: LINQ ve Genel Türler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 8ec2a599a6762d62d101f7660892a6d85a100794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591935"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sorgular, .NET Framework sürüm 2,0 ' de tanıtılan genel türleri temel alır. Sorgu yazmaya başlayabilmeniz için önce genel türler hakkında ayrıntılı bilgi sahibi olmanız gerekmez. Ancak, iki temel kavramı anlamak isteyebilirsiniz:  
  
1. Gibi bir genel koleksiyon sınıfının <xref:System.Collections.Generic.List%601>bir örneğini oluşturduğunuzda, "T" öğesini listenin tutacaksınız nesne türüyle değiştirirsiniz. Örneğin, dizelerin bir listesi olarak `List<string>`ifade edilir ve `Customer` nesne listesi olarak `List<Customer>`ifade edilir. Genel liste kesin bir şekilde yazılır ve öğelerini olarak <xref:System.Object>depolayan koleksiyonlar üzerinde birçok avantaj sağlar. Bir ' a `Customer` `List<string>`eklemeye çalışırsanız, derleme zamanında bir hata alırsınız. Çalışma zamanı türü atama gerçekleştirmeniz zorunda olmadığınızdan genel koleksiyonları kullanmak kolaydır.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>, genel koleksiyon sınıflarının `foreach` ifadesini kullanarak numaralandırılacağını sağlayan arabirimdir. Genel koleksiyon sınıfları, <xref:System.Collections.Generic.IEnumerable%601> destek <xref:System.Collections.IEnumerable>gibi <xref:System.Collections.ArrayList> genel olmayan koleksiyon sınıfları gibi desteklenir.  
  
 Genel türler hakkında daha fazla bilgi için bkz. [Genel türler](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>LINQ sorgularında IEnumerable\> < T değişkenleri  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sorgu değişkenleri, gibi bir <xref:System.Collections.Generic.IEnumerable%601> türetilmiş tür <xref:System.Linq.IQueryable%601>veya olarak yazılır. Olarak `IEnumerable<Customer>`yazılmış bir sorgu değişkeni gördüğünüzde, yalnızca sorgunun çalıştırıldığı zaman, sıfır veya daha fazla `Customer` nesne dizisi üreten anlamına gelir.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyicinin genel tür bildirimleri tanıtıcısına izin verme  
 Tercih ederseniz, [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak genel sözdiziminden kaçınabilirsiniz. Anahtar sözcüğü, derleyiciye, `from` yan tümcesinde belirtilen veri kaynağına bakarak bir sorgu değişkeninin türünü çıkarmasını söyler. `var` Aşağıdaki örnek, önceki örnekle aynı derlenmiş kodu üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var` Anahtar sözcüğü, değişkenin türü belirgin olduğunda veya grup sorguları tarafından üretilenler gibi iç içe geçmiş genel türleri açıkça belirtmek önemli olmadığında yararlıdır. Genel olarak, kullanmanız `var`durumunda kodunuzun başkalarının okuması için daha zor hale yapabileceğini fark ederiz. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](../../generics/index.md)
