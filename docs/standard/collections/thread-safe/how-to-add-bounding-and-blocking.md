---
title: 'Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 33c0b5a93a9c63e3e743a04e69bb7353ac69fa8a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711291"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme
Bu örnek, sınıfında <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> arabirimini uygulayarak ve sonra bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>iç depolama mekanizması olarak bir sınıf örneği kullanarak özel bir koleksiyon sınıfına sınırlama ve engelleme işlevinin nasıl ekleneceğini gösterir. Sınırlama ve engelleme hakkında daha fazla bilgi için bkz. [BlockingCollection genel bakış](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Örnek  
 Özel koleksiyon sınıfı, öncelik düzeylerinin bir <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> nesneleri dizisi olarak temsil edildiği temel bir öncelik kuyruğudur. Her sıra içinde ek sıralama yapılmaz.  
  
 İstemci kodunda, üç görev başlatılır. İlk görev, yürütme sırasında herhangi bir noktada iptali etkinleştirmek üzere klavye vuruşları için yalnızca yoklar. İkinci görev üretici iş parçacığıdır; engelleme koleksiyonuna yeni öğeler ekler ve her öğeye rastgele bir değer temelinde öncelik verir. Üçüncü görev, öğeleri kullanılabilir hale geldiğinde koleksiyondan kaldırır.  
  
 İş parçacıklarından birini diğerinin daha hızlı çalıştırmasını sağlayarak uygulamanın davranışını ayarlayabilirsiniz. Üretici daha hızlı çalışırsa, blok koleksiyon, Oluşturucu üzerinde belirtilen öğelerin sayısını zaten içeriyorsa öğelerin eklenmesini engellediğini fark eder. Tüketici daha hızlı çalışırsa, tüketici yeni bir öğenin eklenmesini beklediği için engelleme işlevini fark edeceksiniz.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Varsayılan olarak, bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> için depolama <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
