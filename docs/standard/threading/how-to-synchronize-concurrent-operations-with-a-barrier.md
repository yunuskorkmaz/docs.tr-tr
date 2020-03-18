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
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137968"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme
Aşağıdaki örnekte, eşzamanlı görevlerin bir <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki programın amacı, sözcükleri yeniden karıştırmak için rasgele bir algoritma kullanarak çözümün yarısını aynı aşamada bulmak için iki iş parçacığı için kaç yineleme (veya aşama) gerektiğini saymaktır. Her iş parçacığı sözcüklerini karıştırdıktan sonra, bariyer faz sonrası işlemi, tümcenin tamamının doğru sözcük sırasına göre işlenmiş olup olmadığını görmek için iki sonucu karşılaştırır.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A, <xref:System.Threading.Barrier> paralel bir işlemdeki tek tek görevlerin tüm görevler engele ulaşıncaya kadar devam etmesini engelleyen bir nesnedir. Aşamalar halinde paralel bir işlem oluştuğunda ve her aşama görevler arasında eşitleme gerektirdiğinde yararlıdır. Bu örnekte, işlemin iki aşaması vardır. İlk aşamada, her görev arabellek kendi bölümünü veri ile doldurur. Her görev kendi bölümünü doldurmayı bitirdiğinde, görev devam etmeye hazır olduğunu bariyere işaret eder ve sonra bekler. Tüm görevler bariyersinyali verdiğinde, engellenir ve ikinci aşama başlar. İkinci aşama, her görevin bu noktaya kadar oluşturulan tüm verilere erişebilmiş olmasını gerektirdiğinden, bariyer gereklidir. Engel olmadan, tamamlaması gereken ilk görevler, diğer görevler tarafından henüz doldurulmamış arabelleklerden okumayı deneyebilir. Bu şekilde istediğiniz sayıda aşamayı eşitleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
