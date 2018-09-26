---
title: 'Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193762"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme
Aşağıdaki örnek, eş zamanlı görevleri ile eşitlemek gösterilmiştir bir <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki program amacı kaç yineleme (veya aşamaları) sayısı için her bulunacak iki iş parçacığı için çözümü kendi yarısında aynı aşamaya sözcük sırasını yeniden ayarlaması randomizing bir algoritma kullanarak gereklidir. Her iş parçacığı, sözcükleri karışık sonra engeli sonrası aşamasını işlemi doğru sözcük sırada işlendikten tam bir cümle görmek için iki sonucu karşılaştırır.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> tüm görevler engel ulaşana kadar devam etmesini bir paralel işlemin içinde tek tek görevler engelleyen bir nesnedir. Bu aşamada paralel işlem gerçekleşir ve her aşamada görevler arasında eşitleme gerektirir yararlı olur. Bu örnekte, işlemi için iki aşaması vardır. İlk aşamada, her görev kendi bölümü arabellek verilerle doldurur. Her görev kendi bölümü doldurma tamamlandığında, görev, devam etmeye hazır engel ve bekler bildirir. Tüm Görevler engel sinyal kullanıcılar, engeli ve ikinci aşaması başlar. İkinci aşama, her görev, bu noktada oluşturulan tüm veri erişimi olmasını gerektirdiğinden engel gereklidir. Engel ilk görevleri tamamlamak için henüz diğer görevler tarafından doldurulmuştur olmayan arabellekler okunacak deneyebilir. Bu aşamada herhangi bir sayıda eşitleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
