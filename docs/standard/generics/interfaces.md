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
ms.openlocfilehash: a6c151798c807206cc7f4b2fbeb21e75e9142379
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46005966"
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu, genel türlerin aileleri arasında ortak işlevselliği sağlayan genel arabirimler genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler tür kullanımı uyumlu seçilen jenerik olmayan arabirimleri sıralama ve eşitlik karşılaştırmaları için ve genel koleksiyon türleri tarafından paylaşılan işlevselliği sağlar.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], tür parametreleri çeşitli genel arabirimlerin birlikte değişen işaretlenmiş veya değişken karşıtı, atama ve kullanarak daha fazla esneklik sağlayan bu arabirimleri uygulayan türleri. Bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları  
 İçinde <xref:System> ad alanı, <xref:System.IComparable%601?displayProperty=nameWithType> ve <xref:System.IEquatable%601?displayProperty=nameWithType> bunların genel olmayan karşılıklarına gibi genel arabirimlerde duyarsızlığı karşılaştırmalarına ve eşitlik karşılaştırmaları sırasıyla sıralama yöntemleri tanımlar. Bu tür karşılaştırmaları gerçekleştirmenize olanak sağlamak için bu arabirimler türleri uygulayın.  
  
 İçinde <xref:System.Collections.Generic> ad alanı, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimleri değil uygulayan türler için bir sıralama veya eşitlik karşılaştırma tanımlamak için bir yol sunan <xref:System.IComparable%601?displayProperty=nameWithType> veya <xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirim ve bunlar için bir yol sağlar Bu ilişkiler yapmak türleri için yeniden tanımlama. Bu arabirimler, yöntemleri ve çoğu genel koleksiyon sınıfların Oluşturucuları tarafından kullanılır. Örneğin, genel geçirebilirsiniz <xref:System.Collections.Generic.IComparer%601> nesnesi oluşturucusuna <xref:System.Collections.Generic.SortedDictionary%602> genel uygulamayan bir tür için bir sıralama düzeni belirlemek için sınıf <xref:System.IComparable%601?displayProperty=nameWithType>. Aşırı yükleme <xref:System.Array.Sort%2A?displayProperty=nameWithType> genel statik yöntem ve <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> sıralamak için örnek yöntem dizi ve listeleri genel kullanma <xref:System.Collections.Generic.IComparer%601> uygulamaları.  
  
 <xref:System.Collections.Generic.Comparer%601> Ve <xref:System.Collections.Generic.EqualityComparer%601> genel sınıfları uygulamaları için temel sınıfları sağlar <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimler ve ayrıca varsayılan sıralama ve eşitlik karşılaştırmaları kendi ilgili aracılığıyla sağlamak <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> ve <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> özellikleri.  
  
### <a name="collection-functionality"></a>Toplama işlevleri  
 <xref:System.Collections.Generic.ICollection%601> Genel arabirimidir temel bir arabirim için genel koleksiyon türleri. Ekleme, kaldırma, kopyalama ve toplamının öğelerini numaralandırma için temel işlevleri sağlar. <xref:System.Collections.Generic.ICollection%601> Her iki genel devralan <xref:System.Collections.Generic.IEnumerable%601> ve jenerik olmayan <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Genel arabirimini genişletir <xref:System.Collections.Generic.ICollection%601> genel arabirim yöntemleriyle dizinli alımı.  
  
 <xref:System.Collections.Generic.IDictionary%602> Genel arabirimini genişletir <xref:System.Collections.Generic.ICollection%601> anahtarlı alımı yöntemleriyle genel arabirim. .NET Framework temel sınıf kitaplığı genel bir sözlük türlere de uygulayabilirsiniz nongeneric <xref:System.Collections.IDictionary> arabirimi.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Genel arabirim genel Numaralandırıcı yapısı sağlar. <xref:System.Collections.Generic.IEnumerator%601> Genel numaralandırıcıların uygulanan genel arabirimi devralır nongeneric <xref:System.Collections.IEnumerator> arabirim; <xref:System.Collections.IEnumerator.MoveNext%2A> ve <xref:System.Collections.IEnumerator.Reset%2A> tür parametresine bağlı olmayan üyeleri `T`, yalnızca nongeneric üzerinde görünür. arabirim. Bu, herhangi bir tüketici jenerik olmayan arabiriminin yönelik genel arabirimi tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Genel Türler](../../../docs/standard/generics/index.md)  
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)  
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)
