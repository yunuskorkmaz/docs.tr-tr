---
title: 'Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 97a95250ff73b43d4404fb891078aed1b04f105e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819740"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme
Aşağıdaki örnek, ile eş zamanlı görevlerin nasıl eşitleneceğini gösterir <xref:System.Threading.Barrier> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki programın amacı, sözcüklerin reshuffle için rastgele bir algoritma kullanarak her biri çözümün yarısını aynı aşamada bulması için iki iş parçacığı için kaç tane yineleme (veya aşama) gerektiğini saymadır. Her bir iş parçacığı, sözcüklerini karmasına başladıktan sonra, ikinci sonuçları, tam tümcenin doğru sözcük düzeninde işlenip işlenmeyeceğini görmek için karşılaştırır.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier>, Bir paralel işlemdeki bireysel görevlerin, tüm görevler Engellene ulaşana kadar devam etmesini önleyen bir nesnedir. Bir paralel işlem aşamalar halinde oluştuğunda ve her aşama görevler arasında eşitleme gerektiriyorsa faydalıdır. Bu örnekte, işlem için iki aşama vardır. İlk aşamada, her görev arabelleğin bölümünü verilerle doldurur. Her görev bölümünün doldurmasını bitirdiğinde, görev engelin devam etmeye hazırlanmasına işaret eder ve sonra bekler. Tüm görevler engeli işaret ettikleri zaman engellenmemiş ve ikinci aşama başlatılır. İkinci aşama, her görevin bu noktada oluşturulan tüm verilere erişmesini gerektirdiğinden, engeli gereklidir. Engel olmadan, tamamlanacak ilk görevler henüz başka görevler tarafından doldurulmamış olan arabelleklerden okumayı deneyebilir. Herhangi bir sayıda aşamayı bu şekilde eşzamanlı hale getirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama için veri yapıları](../parallel-programming/data-structures-for-parallel-programming.md)
