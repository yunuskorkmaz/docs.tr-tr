---
title: LINQ ve Genel Türler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 9a2d1ac72f70e7cd314d349e81ab2bc815a5bf13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635580"
---
# <a name="linq-and-generic-types-c"></a>LINQ ve Genel Türler (C#)
LINQ sorguları, .NET Framework'ün 2.0 sürümünde tanıtılan genel türleri temel almaktadır. Sorgu yazmaya başlamadan önce jenerik hakkında derinlemesine bilgi sahibi olmanız gerekmez. Ancak, iki temel kavramları anlamak isteyebilirsiniz:  
  
1. "T" gibi <xref:System.Collections.Generic.List%601>genel bir koleksiyon sınıfı örneği oluşturduğunuzda, listenin tutacağı nesne türüyle "T"yi değiştirirsiniz. Örneğin, dizeler in bir listesi `List<string>`olarak ifade `Customer` edilir ve nesnelerin `List<Customer>`listesi olarak ifade edilir. Genel bir liste güçlü bir şekilde dizilir ve öğelerini <xref:System.Object>. A'ya `Customer` `List<string>`bir eklemeye çalışırsanız, derleme zamanında bir hata alırsınız. Çalışma zamanı tür döküm gerçekleştirmek zorunda olmadığını zedebilirsiniz, çünkü genel koleksiyonları kullanmak kolaydır.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>`foreach` genel toplama sınıflarının ifade kullanılarak numaralandırılmasını sağlayan arabirimdir. Genel toplama <xref:System.Collections.Generic.IEnumerable%601> sınıfları, destek gibi genel <xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable>olmayan toplama sınıfları gibi destekler.  
  
 Jenerikler hakkında daha fazla bilgi için [Bkz. Generics.](../../generics/index.md)  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>LINQ Sorgularında T\> değişkenleri<Tanımlanabilir  
 LINQ sorgu değişkenleri olarak <xref:System.Collections.Generic.IEnumerable%601> veya türemiş <xref:System.Linq.IQueryable%601>türde olarak yazılır. `IEnumerable<Customer>`Olarak yazılan bir sorgu değişkeni gördüğünüzde, bu yalnızca sorgunun yürütüldüğünde sıfır veya daha `Customer` fazla nesneden oluşan bir dizi oluşturacağı anlamına gelir.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Daha fazla bilgi için [LINQ Sorgu İşlemlerinde Tür İlişkileri'ne](./type-relationships-in-linq-query-operations.md)bakın.  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Derleyicinin Genel Tür Bildirimlerini işlemesine izin verme  
 İsterseniz, [var](../../../language-reference/keywords/var.md) anahtar sözcük lerini kullanarak genel sözdizimini önleyebilirsiniz. Anahtar `var` kelime, `from` derleyiciye, yan tümcede belirtilen veri kaynağına bakarak sorgu değişkeninin türünü çıkarmasını söyler. Aşağıdaki örnek, önceki örnekle aynı derlenmiş kodu üretir:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 Anahtar `var` kelime, değişkenin türü açık olduğunda veya grup sorguları tarafından üretilenler gibi iç içe gelişmiş genel türleri açıkça belirtmek önemli olmadığında yararlıdır. Genel olarak, kullanıyorsanız, `var`kodunuzun başkalarının okumasını zorlaştırabileceğini fark etmenizi öneririz. Daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](../../generics/index.md)
