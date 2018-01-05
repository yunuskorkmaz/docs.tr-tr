---
title: "Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7fe57d99382c3472d0af5e5f64f7b237692b921b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme
Bu örnek sınırlama ve engelleme işlevi bir özel koleksiyon sınıfına uygulayarak nasıl ekleneceğini gösterir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> arabirim sınıfında ve dahili depolama mekanizması olarak bir sınıf örneği kullanarak bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Sınırlama ve engelleme hakkında daha fazla bilgi için bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Örnek  
 Özel koleksiyon sınıfı içinde öncelik düzeyleri temsil edilen bir dizi gibi bir temel öncelik sırasıdır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> nesneleri. Hiçbir ek sıralama her sıra içinde gerçekleştirilir.  
  
 İstemci kodu üç görev başlatıldı. Yürütme sırasında herhangi bir noktada iptal etkinleştirmek için klavye vuruşları için ilk görev yalnızca yoklar. İkinci görev üretici parçacığıdır; engelleme koleksiyona yeni öğeler ekler ve her bir öğeyi rastgele bir değere göre bir öncelik verir. Üçüncü görev öğeleri kullanılabilir olduklarında koleksiyondan kaldırır.  
  
 Diğer daha hızlı çalıştırma iş parçacığı birini yaparak uygulama davranışına göre ayarlayabilirsiniz. Üretici daha hızlı çalıştırıyorsa, bu zaten oluşturucuda belirtilen öğe sayısını içeriyorsa eklenmesini öğeleri engelleme koleksiyonu engeller gibi sınırlayıcı işlevselliği fark edeceksiniz. Tüketici daha hızlı çalıştırıyorsa, engelleme işlevine tüketici olarak eklenmesi için yeni bir öğe için bekleyeceği fark edeceksiniz.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Varsayılan olarak, depolama alanı için bir <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> olan <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)
