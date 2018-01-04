---
title: "Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 616229abed93c6793b392724d038d8f9160cd6ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme
Aşağıdaki örnek, eş zamanlı görevleri ile eşitlemek gösterilmiştir bir <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki programı amacı kaç yineleme (veya aşamaları) sayısı için her bulma için iki iş parçacığı için çözümü kendi yarısı aynı aşamaya sözcükleri sırasını yeniden ayarlaması randomizing bir algoritma kullanarak gereken budur. Her iş parçacığının kendi sözcükler karışık sonra engel sonrası aşaması işlemi tam bir cümle doğru word sırada işlenip işlenmediğini görmek için iki sonucu karşılaştırır.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> tüm görevler engel ulaşana kadar devam etmeden bir paralel işlemin tek tek görevlere engelleyen bir nesnedir. Paralel işlem aşamada gerçekleşir ve her aşamada görevler arasında eşitleme gerektirdiğinde yararlı olacaktır. Bu örnekte, işlem için iki aşama vardır. İlk aşamada, her görev kendi bölümüne arabellek verilerle doldurur. Her görev kendi bölümüne doldurma tamamlandığında, görev devam etmeye hazır engel ve bekler işaret eder. Tüm Görevler engel işaret engeli ve ikinci aşaması başlar. İkinci aşama her görev, bu noktaya kadar üretilen tüm verilere erişimi olmasını gerektirdiğinden engel gereklidir. Engel ilk görevlerinin tamamlanması için henüz diğer görevler tarafından doldurulmuştur olmayan arabellekler okunacak deneyebilirsiniz. Bu şekilde aşamada herhangi bir sayıda eşitleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
