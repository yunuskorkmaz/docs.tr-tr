---
title: Genel Arabirimler
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71cc1410a13fc73cce931a063a929ba94aab91be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces"></a>Genel Arabirimler
Bu konu genel türler aileleri arasında ortak işlevsellik sağlayan genel arabirimler genel bir bakış sağlar.  
  
## <a name="generic-interfaces"></a>Genel Arabirimler  
 Genel arabirimler tür kullanımı uyumlu ortaklarınıza nongeneric arabirimlerine sıralama ve eşitlik karşılaştırmaları ve genel koleksiyon türleri tarafından paylaşılan işlevselliği sağlar.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], birkaç genel arabirimler tür parametrelerini eşdeğişken işaretlenmiş veya karşıtı atama ve kullanarak daha fazla esneklik sağlayan, bu arabirimleri uygulayan türleri. Bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları  
 İçinde <xref:System> ad alanı, <xref:System.IComparable%601?displayProperty=nameWithType> ve <xref:System.IEquatable%601?displayProperty=nameWithType> nongeneric dekiler gibi genel arabirimler karşılaştırmaları ve eşitlik karşılaştırmaları sırasıyla sıralama yöntemlerini tanımlar. Türleri gibi karşılaştırmaları gerçekleştirmenize olanak sağlamak için bu arabirimlerini uygular.  
  
 İçinde <xref:System.Collections.Generic> ad alanı, <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimler uygulamayan türleri için bir sıralama veya eşitlik karşılaştırması tanımlamak için bir yol sunan <xref:System.IComparable%601?displayProperty=nameWithType> veya <xref:System.IEquatable%601?displayProperty=nameWithType> genel arabirim ve bunlar için bir yol sağlar Bu ilişkileri yapmak türleri için yeniden tanımlayın. Bu arabirimleri yöntemleri ve çoğu genel koleksiyon sınıfların oluşturucular tarafından kullanılır. Örneğin, bir genel geçirebilirsiniz <xref:System.Collections.Generic.IComparer%601> oluşturucusunun nesnesine <xref:System.Collections.Generic.SortedDictionary%602> genel uygulamayan bir tür için bir sıralama düzeni belirlemek için sınıf <xref:System.IComparable%601?displayProperty=nameWithType>. Aşırı <xref:System.Array.Sort%2A?displayProperty=nameWithType> genel statik yöntem ve <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> sıralamak için örnek yöntemi dizi ve listeleri genel kullanma <xref:System.Collections.Generic.IComparer%601> uygulamaları.  
  
 <xref:System.Collections.Generic.Comparer%601> Ve <xref:System.Collections.Generic.EqualityComparer%601> genel sınıfları uygulamaları için temel sınıfları sağlar <xref:System.Collections.Generic.IComparer%601> ve <xref:System.Collections.Generic.IEqualityComparer%601> genel arabirimler ve ayrıca varsayılan sıralama ve eşitlik karşılaştırmaları kendi ilgili aracılığıyla sağlamak <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> ve <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> özellikleri.  
  
### <a name="collection-functionality"></a>Toplama işlevleri  
 <xref:System.Collections.Generic.ICollection%601> Genel arabirimidir genel koleksiyon türleri için temel arabirimi. Ekleme, kaldırma, kopyalama ve toplamının öğelerini numaralandırma için temel işlevleri sağlar. <xref:System.Collections.Generic.ICollection%601>Her iki genel devralır <xref:System.Collections.Generic.IEnumerable%601> ve nongeneric <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Genel arabirimi genişletiyor <xref:System.Collections.Generic.ICollection%601> dizinli alma yöntemleriyle genel arabirim.  
  
 <xref:System.Collections.Generic.IDictionary%602> Genel arabirimi genişletiyor <xref:System.Collections.Generic.ICollection%601> anahtarlı alma yöntemleriyle genel arabirim. .NET Framework temel sınıf kitaplığı'nda genel sözlük türleri de nongeneric uygulamak <xref:System.Collections.IDictionary> arabirimi.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Genel arabirim genel Numaralandırıcı yapısı sağlar. <xref:System.Collections.Generic.IEnumerator%601> Genel numaralandırıcıların uygulanan genel arabirimi devralır nongeneric <xref:System.Collections.IEnumerator> arabirim; <xref:System.Collections.IEnumerator.MoveNext%2A> ve <xref:System.Collections.IEnumerator.Reset%2A> tür parametresi dayanmayan üyeleri `T`, yalnızca üzerinde nongeneric görünür arabirim. Bu, tüm tüketici nongeneric arabiriminin genel arabirim tüketebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genel türler](../../../docs/standard/generics/index.md)  
 [.NET Framework'teki genel koleksiyonlar](../../../docs/standard/generics/collections.md)  
 [Dizi ve listeleri düzenlemek için genel temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)
