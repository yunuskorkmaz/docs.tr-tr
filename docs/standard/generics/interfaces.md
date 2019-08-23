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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09e9a51fe9c1fd25a6791cf924180329718138c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915887"
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu, genel türlerde ailelerde ortak işlevsellik sağlayan genel arabirimlere genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler, sıralama ve eşitlik karşılaştırmaları ve genel koleksiyon türleri tarafından paylaşılan işlevler için genel olmayan arabirimlere tür açısından güvenli bir karşılıkları sağlar.  
  
> [!NOTE]
> .NET Framework 4 ' ten başlayarak, bazı genel arabirimlerin tür parametreleri birlikte değişken veya değişken karşıtı olarak işaretlenir ve bu arabirimleri uygulayan türler atanırken ve kullanılırken daha fazla esneklik sağlar. Bkz. [Kovaryans ve değişken varyansı](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları  
 Ad alanında, genel olmayan karşılıkları <xref:System.IEquatable%601?displayProperty=nameWithType> gibi vegenelarabirimlersırasıylakarşılaştırmalarıveeşitlikkarşılaştırmalarısıralamayöntemlerinitanımlar.<xref:System.IComparable%601?displayProperty=nameWithType> <xref:System> Türler bu arabirimleri, bu tür karşılaştırmaları gerçekleştirme yeteneği sağlamak için uygular.  
  
 <xref:System.Collections.Generic> Ad <xref:System.IComparable%601?displayProperty=nameWithType> alanında <xref:System.Collections.Generic.IComparer%601> , ve<xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimleri, veya<xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirimini uygulamayan türler için bir sıralama ya da eşitlik karşılaştırması tanımlamak için bir yol sağlar ve Bunu yapan türler için bu ilişkileri yeniden tanımlayın. Bu arabirimler, genel koleksiyon sınıflarının birçoğunun yöntemleri ve oluşturucuları tarafından kullanılır. Örneğin, genel bir <xref:System.Collections.Generic.IComparer%601> nesneyi, genel <xref:System.IComparable%601?displayProperty=nameWithType>uygulamayan bir tür için sıralama düzeni belirtmek <xref:System.Collections.Generic.SortedDictionary%602> üzere sınıfının oluşturucusuna geçirebilirsiniz. Genel statik yöntemin aşırı yüklemeleri <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> ve genel <xref:System.Collections.Generic.IComparer%601> uygulamaları kullanarak dizileri ve listeleri sıralamak için örnek yöntemi vardır.  
  
 <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> Ve genel sınıfları, ve<xref:System.Collections.Generic.IEqualityComparer%601> genel arayüzlerinin uygulamaları için temel sınıflar sağlar ve ayrıca bunlara karşılık gelen varsayılan sıralama ve eşitlik karşılaştırmaları sağlar <xref:System.Collections.Generic.EqualityComparer%601> <xref:System.Collections.Generic.Comparer%601> ve <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> özellikleri.  
  
### <a name="collection-functionality"></a>Koleksiyon Işlevselliği  
 <xref:System.Collections.Generic.ICollection%601> Genel arabirim, genel koleksiyon türleri için temel arabirimdir. Öğe ekleme, kaldırma, kopyalama ve numaralandırma için temel işlevleri sağlar. <xref:System.Collections.Generic.ICollection%601>hem genel <xref:System.Collections.Generic.IEnumerable%601> hem de genel <xref:System.Collections.IEnumerable>olmayan uygulamalardan devralır.  
  
 Genel arabirim, <xref:System.Collections.Generic.ICollection%601> genel arabirimi dizinli alma yöntemleriyle genişletir. <xref:System.Collections.Generic.IList%601>  
  
 Genel arabirim, <xref:System.Collections.Generic.ICollection%601> genel arabirimi anahtarlı alma yöntemleriyle genişletir. <xref:System.Collections.Generic.IDictionary%602> .NET Framework temel sınıf kitaplığındaki genel sözlük türleri genel <xref:System.Collections.IDictionary> olmayan arabirimi de uygular.  
  
 Genel <xref:System.Collections.Generic.IEnumerable%601> arabirim, genel bir Numaralandırıcı yapısı sağlar. <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.MoveNext%2A> Genel Numaralandırıcılar tarafından uygulanan `T`genel arabirim, genel olmayan arabirimi devralır; tür parametresine bağlı olmayan ve üyeleri yalnızca genel olmayan <xref:System.Collections.Generic.IEnumerator%601> arayüz. Bu, genel olmayan arabirimin herhangi bir tüketicisinin genel arabirimi de tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)
