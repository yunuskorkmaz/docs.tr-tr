---
title: Genel Arabirimler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
ms.openlocfilehash: 704ada32d428c468d5b71a3f1390568ca586079e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708330"
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu, genel türlerin aileleri arasında ortak işlevsellik sağlayan genel arabirimlere genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler, sipariş ve eşitlik karşılaştırmaları ve genel koleksiyon türleri tarafından paylaşılan işlevsellik için genel olmayan arabirimlere tür güvenli karşıtlıklar sağlar.  
  
> [!NOTE]
> .NET Framework 4'ten başlayarak, birkaç genel arabirimin tür parametreleri eşdeğişken veya kontrdeğişken olarak işaretlenir ve bu arabirimleri uygulayan türleri atama ve kullanmada daha fazla esneklik sağlar. [Bkz. Covariance ve Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve Sipariş Karşılaştırmaları  
 <xref:System> Ad alanında, <xref:System.IComparable%601?displayProperty=nameWithType> genel olmayan karşılıkları gibi genel <xref:System.IEquatable%601?displayProperty=nameWithType> olmayan arabirimler, sırasıyla karşılaştırmalar ve eşitlik karşılaştırmaları sıralama yöntemleri tanımlar. Türleri bu tür karşılaştırmalar gerçekleştirmek için yeteneği sağlamak için bu arabirimleri uygular.  
  
 <xref:System.Collections.Generic> Ad alanında, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimler veya <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirimi uygulamayan türler için bir sıralama veya eşitlik karşılaştırması tanımlamak için bir yol sunar ve bunu yapan türler için bu ilişkileri yeniden tanımlamak için bir yol sağlar. Bu arabirimler, genel toplama sınıflarının çoğunun yöntemleri ve oluşturucuları tarafından kullanılır. Örneğin, genel <xref:System.Collections.Generic.IComparer%601> <xref:System.IComparable%601?displayProperty=nameWithType>olarak uygulanmayan bir tür için <xref:System.Collections.Generic.SortedDictionary%602> bir sıralama sırası belirtmek için genel bir nesneyi sınıfın oluşturucusuna geçirebilirsiniz. <xref:System.Array.Sort%2A?displayProperty=nameWithType> Genel statik yöntem ve genel <xref:System.Collections.Generic.IComparer%601> uygulamaları kullanarak dizileri ve listeleri sıralamak için <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> örnek yöntemi overloads vardır.  
  
 <xref:System.Collections.Generic.Comparer%601> <xref:System.Collections.Generic.EqualityComparer%601> Ve genel sınıflar <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimlerin uygulamaları için temel sınıflar sağlar ve aynı zamanda kendi <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> ilgili <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> ve özellikleri üzerinden varsayılan sıralama ve eşitlik karşılaştırmaları sağlar.  
  
### <a name="collection-functionality"></a>Koleksiyon İşlevselliği  
 Genel <xref:System.Collections.Generic.ICollection%601> arabirim, genel toplama türleri için temel arabirimdir. Öğeleri eklemek, kaldırmak, kopyalamak ve kopyalamak için temel işlevsellik sağlar. <xref:System.Collections.Generic.ICollection%601>hem genel <xref:System.Collections.Generic.IEnumerable%601> hem de <xref:System.Collections.IEnumerable>genel olmayan devralır.  
  
 Genel <xref:System.Collections.Generic.IList%601> arabirim, <xref:System.Collections.Generic.ICollection%601> dizinlenmiş alma yöntemleriyle genel arabirimi genişletir.  
  
 Genel <xref:System.Collections.Generic.IDictionary%602> arabirim, <xref:System.Collections.Generic.ICollection%601> anahtarlı alma yöntemleriyle genel arabirimi genişletir. .NET Framework base sınıf kitaplığındaki genel sözlük <xref:System.Collections.IDictionary> türleri de genel olmayan arabirimi uygular.  
  
 Genel <xref:System.Collections.Generic.IEnumerable%601> arabirim genel bir sayısallaştırıcı yapı sağlar. <xref:System.Collections.Generic.IEnumerator%601> Genel sayısallaştırıcılar tarafından uygulanan genel arabirim, <xref:System.Collections.IEnumerator> genel olmayan arabirimi devralır; <xref:System.Collections.IEnumerator.MoveNext%2A> ve <xref:System.Collections.IEnumerator.Reset%2A> tür parametresine `T`bağlı olmayan üyeler, yalnızca genel olmayan arabirimde görünür. Bu, genel olmayan arabirimin herhangi bir tüketicide de genel arabirimi tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Covariance ve Kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
