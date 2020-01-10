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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708330"
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu, genel türlerde ailelerde ortak işlevsellik sağlayan genel arabirimlere genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler, sıralama ve eşitlik karşılaştırmaları ve genel koleksiyon türleri tarafından paylaşılan işlevler için genel olmayan arabirimlere tür açısından güvenli bir karşılıkları sağlar.  
  
> [!NOTE]
> .NET Framework 4 ' ten başlayarak, bazı genel arabirimlerin tür parametreleri birlikte değişken veya değişken karşıtı olarak işaretlenir ve bu arabirimleri uygulayan türler atanırken ve kullanılırken daha fazla esneklik sağlar. Bkz. [Kovaryans ve değişken varyansı](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları  
 <xref:System> ad alanında, genel olmayan karşılıkları gibi <xref:System.IComparable%601?displayProperty=nameWithType> ve <xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirimleri sırasıyla karşılaştırmaları ve eşitlik karşılaştırmaları sıralama yöntemlerini tanımlar. Türler bu arabirimleri, bu tür karşılaştırmaları gerçekleştirme yeteneği sağlamak için uygular.  
  
 <xref:System.Collections.Generic> ad alanında, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimleri, <xref:System.IComparable%601?displayProperty=nameWithType> veya <xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirimini uygulamayan türler için bir sıralama ya da eşitlik karşılaştırması tanımlamak için bir yol sunar ve bunu yapan türler için bu ilişkileri yeniden tanımlamak için bir yol sağlar. Bu arabirimler, genel koleksiyon sınıflarının birçoğunun yöntemleri ve oluşturucuları tarafından kullanılır. Örneğin, genel bir <xref:System.Collections.Generic.IComparer%601> nesnesini, genel <xref:System.IComparable%601?displayProperty=nameWithType>uygulamayan bir tür için sıralama düzeni belirtmek üzere <xref:System.Collections.Generic.SortedDictionary%602> sınıfının oluşturucusuna geçirebilirsiniz. <xref:System.Array.Sort%2A?displayProperty=nameWithType> genel statik yönteminin aşırı yüklemeleri ve genel <xref:System.Collections.Generic.IComparer%601> uygulamalarını kullanarak dizileri ve listeleri sıralamak için <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> örnek yöntemi vardır.  
  
 <xref:System.Collections.Generic.Comparer%601> ve <xref:System.Collections.Generic.EqualityComparer%601> genel sınıfları, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimlerin uygulamalarına yönelik temel sınıflar sağlar ve ayrıca ilgili <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> ve <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> özellikleri aracılığıyla varsayılan sıralama ve eşitlik karşılaştırmaları sağlar.  
  
### <a name="collection-functionality"></a>Koleksiyon Işlevselliği  
 <xref:System.Collections.Generic.ICollection%601> genel arabirim, genel koleksiyon türleri için temel arabirimdir. Öğe ekleme, kaldırma, kopyalama ve numaralandırma için temel işlevleri sağlar. <xref:System.Collections.Generic.ICollection%601> hem genel <xref:System.Collections.Generic.IEnumerable%601> hem de genel olmayan <xref:System.Collections.IEnumerable>devralır.  
  
 <xref:System.Collections.Generic.IList%601> genel arabirimi, <xref:System.Collections.Generic.ICollection%601> genel arabirimi dizinli alma yöntemleriyle genişletir.  
  
 <xref:System.Collections.Generic.IDictionary%602> genel arabirimi, <xref:System.Collections.Generic.ICollection%601> genel arabirimini anahtarlı alma yöntemleriyle genişletir. .NET Framework temel sınıf kitaplığındaki genel sözlük türleri genel olmayan <xref:System.Collections.IDictionary> arabirimini de uygular.  
  
 <xref:System.Collections.Generic.IEnumerable%601> genel arabirimi genel bir Numaralandırıcı yapısı sağlar. Genel Numaralandırıcılar tarafından uygulanan <xref:System.Collections.Generic.IEnumerator%601> genel arabirim, genel olmayan <xref:System.Collections.IEnumerator> arabirimini devralır; tür parametresi `T`bağımlı olmayan <xref:System.Collections.IEnumerator.MoveNext%2A> ve <xref:System.Collections.IEnumerator.Reset%2A> Üyeler yalnızca genel olmayan arabirimde görünür. Bu, genel olmayan arabirimin herhangi bir tüketicisinin genel arabirimi de tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)
