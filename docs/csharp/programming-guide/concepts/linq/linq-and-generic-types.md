---
title: LINQ ve Genel Türler (C#)
description: Sorguları destekleyen C# ' de genel türlerin temel kavramları hakkında bilgi edinin.  LINQ sorguları genel türleri temel alır.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 98054a4a21704293faa1194dac342bc48aef138d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165646"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
LINQ sorguları, .NET Framework sürüm 2,0 ' de tanıtılan genel türleri temel alır. Sorgu yazmaya başlayabilmeniz için önce genel türler hakkında ayrıntılı bilgi sahibi olmanız gerekmez. Ancak, iki temel kavramı anlamak isteyebilirsiniz:  
  
1. Gibi bir genel koleksiyon sınıfının bir örneğini oluşturduğunuzda <xref:System.Collections.Generic.List%601> , "T" öğesini listenin tutacaksınız nesne türüyle değiştirirsiniz. Örneğin, dizelerin bir listesi olarak ifade edilir `List<string>` ve `Customer` nesne listesi olarak ifade edilir `List<Customer>` . Genel liste kesin bir şekilde yazılır ve öğelerini olarak depolayan koleksiyonlar üzerinde birçok avantaj sağlar <xref:System.Object> . Bir `Customer` ' a eklemeye çalışırsanız `List<string>` , derleme zamanında bir hata alırsınız. Çalışma zamanı türü atama gerçekleştirmeniz zorunda olmadığınızdan genel koleksiyonları kullanmak kolaydır.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>, genel koleksiyon sınıflarının ifadesini kullanarak numaralandırılacağını sağlayan arabirimdir `foreach` . Genel koleksiyon sınıfları, <xref:System.Collections.Generic.IEnumerable%601> destek gibi genel olmayan koleksiyon sınıfları gibi desteklenir <xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable> .  
  
 Genel türler hakkında daha fazla bilgi için bkz. [Genel türler](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>LINQ sorgularında IEnumerable<T \> değişkenleri  
 LINQ sorgu değişkenleri, gibi <xref:System.Collections.Generic.IEnumerable%601> bir türetilmiş tür veya olarak yazılır <xref:System.Linq.IQueryable%601> . Olarak yazılmış bir sorgu değişkeni gördüğünüzde, `IEnumerable<Customer>` yalnızca sorgunun çalıştırıldığı zaman, sıfır veya daha fazla nesne dizisi üreten anlamına gelir `Customer` .  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyicinin genel tür bildirimleri tanıtıcısına izin verme  
 Tercih ederseniz, [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak genel sözdiziminden kaçınabilirsiniz. `var`Anahtar sözcüğü, derleyiciye, yan tümcesinde belirtilen veri kaynağına bakarak bir sorgu değişkeninin türünü çıkarmasını söyler `from` . Aşağıdaki örnek, önceki örnekle aynı derlenmiş kodu üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var`Anahtar sözcüğü, değişkenin türü belirgin olduğunda veya grup sorguları tarafından üretilenler gibi iç içe geçmiş genel türleri açıkça belirtmek önemli olmadığında yararlıdır. Genel olarak, kullanmanız durumunda `var` kodunuzun başkalarının okuması için daha zor hale yapabileceğini fark ederiz. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](../../generics/index.md)
