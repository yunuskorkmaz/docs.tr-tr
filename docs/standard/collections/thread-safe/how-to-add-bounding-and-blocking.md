---
title: 'Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470427"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme
Bu örnekte, sınırlama ve engelleme işlevi bir özel koleksiyon sınıfına uygulayarak ekleme işlemi açıklanır <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> arabirim sınıfı ve ardından dahili depolama mekanizması olarak bir sınıf örneği kullanarak bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Sınırlama ve engelleme hakkında daha fazla bilgi için bkz. [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Örnek  
 Özel koleksiyon sınıfı bir dizi olarak öncelik düzeyleri gösterilir bir temel öncelik sırasıdır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> nesneleri. Ek bir sıralama yok, her bir kuyruk içinde gerçekleştirilir.  
  
 İstemci kod içinde üç görevler oluşturulduklarında başlatılır. İlk görev yürütme sırasında herhangi bir noktada iptal etkinleştirmek klavye vuruşları için yalnızca yoklar. İkinci görev üretici parçacığıdır; Bu engelleme koleksiyona yeni öğeler ekler ve her bir öğe rastgele bir değere göre bir öncelik verir. Üçüncü görev öğeleri kullanıma sunuldukça koleksiyondan kaldırır.  
  
 İş parçacıklarından diğerinden daha hızlı çalışır hale getirerek, uygulamanın davranışı ayarlayabilirsiniz. Üretici daha hızlı çalışır, engelleyici koleksiyon öğeleri, zaten oluşturucuda belirtilen öğe sayısını içeriyorsa eklenmelerini önler olarak sınırlayıcı işlevselliğini fark edeceksiniz. Tüketici daha hızlı çalışır, yeni bir öğe eklenmesi tüketici engelleme işlevleri bekler fark edeceksiniz.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Varsayılan olarak, depolama alanı için bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> olduğu <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
