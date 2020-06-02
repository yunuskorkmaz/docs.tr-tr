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
ms.openlocfilehash: 21a244a5d44b036a987d8eb8a79aef2c4b8e9a76
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287525"
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu, genel türlerde ailelerde ortak işlevsellik sağlayan genel arabirimlere genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler, sıralama ve eşitlik karşılaştırmaları ve genel koleksiyon türleri tarafından paylaşılan işlevler için genel olmayan arabirimlere tür açısından güvenli bir karşılıkları sağlar.  
  
> [!NOTE]
> .NET Framework 4 ' ten başlayarak, bazı genel arabirimlerin tür parametreleri birlikte değişken veya değişken karşıtı olarak işaretlenir ve bu arabirimleri uygulayan türler atanırken ve kullanılırken daha fazla esneklik sağlar. Bkz. [Kovaryans ve değişken varyansı](covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları  
 <xref:System>Ad alanında, <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> genel olmayan karşılıkları gibi ve genel arabirimler sırasıyla karşılaştırmaları ve eşitlik karşılaştırmaları sıralama yöntemlerini tanımlar. Türler bu arabirimleri, bu tür karşılaştırmaları gerçekleştirme yeteneği sağlamak için uygular.  
  
 <xref:System.Collections.Generic>Ad alanında, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimleri, veya genel arabirimini uygulamayan türler için bir sıralama ya da eşitlik karşılaştırması tanımlamak için bir yol sunar <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> ve bunu yapan türler için bu ilişkileri yeniden tanımlamak için bir yol sağlar. Bu arabirimler, genel koleksiyon sınıflarının birçoğunun yöntemleri ve oluşturucuları tarafından kullanılır. Örneğin, genel bir <xref:System.Collections.Generic.IComparer%601> nesneyi, <xref:System.Collections.Generic.SortedDictionary%602> genel uygulamayan bir tür için sıralama düzeni belirtmek üzere sınıfının oluşturucusuna geçirebilirsiniz <xref:System.IComparable%601?displayProperty=nameWithType> . Genel statik yöntemin aşırı yüklemeleri <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> genel uygulamaları kullanarak dizileri ve listeleri sıralamak için örnek yöntemi vardır <xref:System.Collections.Generic.IComparer%601> .  
  
 <xref:System.Collections.Generic.Comparer%601>Ve <xref:System.Collections.Generic.EqualityComparer%601> Genel sınıfları, ve genel arabirimlerinin uygulamaları için temel sınıflar <xref:System.Collections.Generic.IComparer%601> sağlar <xref:System.Collections.Generic.IEqualityComparer%601> ve ayrıca, ilgili ve özellikleri aracılığıyla varsayılan sıralama ve eşitlik karşılaştırmaları sağlar <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> .  
  
### <a name="collection-functionality"></a>Koleksiyon Işlevselliği  
 <xref:System.Collections.Generic.ICollection%601>Genel arabirim, genel koleksiyon türleri için temel arabirimdir. Öğe ekleme, kaldırma, kopyalama ve numaralandırma için temel işlevleri sağlar. <xref:System.Collections.Generic.ICollection%601>hem genel hem de <xref:System.Collections.Generic.IEnumerable%601> genel olmayan uygulamalardan devralır <xref:System.Collections.IEnumerable> .  
  
 <xref:System.Collections.Generic.IList%601>Genel arabirim, <xref:System.Collections.Generic.ICollection%601> genel arabirimi dizinli alma yöntemleriyle genişletir.  
  
 <xref:System.Collections.Generic.IDictionary%602>Genel arabirim, <xref:System.Collections.Generic.ICollection%601> genel arabirimi anahtarlı alma yöntemleriyle genişletir. .NET Framework temel sınıf kitaplığındaki genel sözlük türleri genel olmayan arabirimi de uygular <xref:System.Collections.IDictionary> .  
  
 <xref:System.Collections.Generic.IEnumerable%601>Genel arabirim, genel bir Numaralandırıcı yapısı sağlar. Genel <xref:System.Collections.Generic.IEnumerator%601> Numaralandırıcılar tarafından uygulanan genel arabirim, genel olmayan <xref:System.Collections.IEnumerator> arabirimi devralır; <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator.Reset%2A> tür parametresine bağlı olmayan ve üyeleri `T` yalnızca genel olmayan arabirimde görünür. Bu, genel olmayan arabirimin herhangi bir tüketicisinin genel arabirimi de tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](index.md)
- [.NET Framework'teki Genel Koleksiyonlar](collections.md)
- [Dizileri ve listeleri Işlemek için genel Temsilciler](delegates-for-manipulating-arrays-and-lists.md)
- [Kovaryans ve değişken sapması](covariance-and-contravariance.md)
