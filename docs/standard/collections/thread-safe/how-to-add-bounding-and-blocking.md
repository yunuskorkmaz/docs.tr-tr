---
title: 'Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 33c0b5a93a9c63e3e743a04e69bb7353ac69fa8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711291"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme
Bu örnek, sınıfta <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> arabirimi uygulayarak özel bir koleksiyon sınıfına bağlama ve engelleme işlevinin nasıl ekleyeceğini ve bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>sınıf örneğini bir . için iç depolama mekanizması olarak nasıl kullanacağını gösterir. Sınırlama ve engelleme hakkında daha fazla bilgi için [bkz.](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)  
  
## <a name="example"></a>Örnek  
 Özel toplama sınıfı, öncelik düzeylerinin <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> bir nesne dizisi olarak temsil edildiği temel öncelik sırasıdır. Her kuyruğa ek sipariş yapılmaz.  
  
 İstemci kodunda üç görev başlatılır. İlk görev, yürütme sırasında herhangi bir noktada iptali etkinleştirmek için klavye vuruşlarını anketler. İkinci görev üretici iş parçacığı; engelleme koleksiyonuna yeni öğeler ekler ve her öğeye rasgele bir değere dayalı bir öncelik verir. Üçüncü görev, kullanılabilir olduklarında öğeleri koleksiyondan kaldırır.  
  
 İş parçacıklarından birinin diğerinden daha hızlı çalışmasını sağlayarak uygulamanın davranışını ayarlayabilirsiniz. Üretici daha hızlı çalışırsa, engelleme koleksiyonu zaten oluşturucuda belirtilen öğe sayısını içeriyorsa maddelerin eklenmesini önlediği için sınırlama işlevini fark esiniz. Tüketici daha hızlı çalışırsa, tüketici yeni bir öğenin eklenmesini beklerken engelleme işlevini fark esiniz.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Varsayılan olarak, a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> için <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>depolama .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
