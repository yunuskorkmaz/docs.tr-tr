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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137968"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme
Aşağıdaki örnek, eş zamanlı görevlerin bir <xref:System.Threading.Barrier>nasıl eşitleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki programın amacı, sözcüklerin reshuffle için rastgele bir algoritma kullanarak her biri çözümün yarısını aynı aşamada bulması için iki iş parçacığı için kaç tane yineleme (veya aşama) gerektiğini saymadır. Her bir iş parçacığı, sözcüklerini karmasına başladıktan sonra, ikinci sonuçları, tam tümcenin doğru sözcük düzeninde işlenip işlenmeyeceğini görmek için karşılaştırır.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier>, tüm görevler Engellene ulaşana kadar paralel işlemdeki bireysel görevlerin devam etmesini önleyen bir nesnedir. Bir paralel işlem aşamalar halinde oluştuğunda ve her aşama görevler arasında eşitleme gerektiriyorsa faydalıdır. Bu örnekte, işlem için iki aşama vardır. İlk aşamada, her görev arabelleğin bölümünü verilerle doldurur. Her görev bölümünün doldurmasını bitirdiğinde, görev engelin devam etmeye hazırlanmasına işaret eder ve sonra bekler. Tüm görevler engeli işaret ettikleri zaman engellenmemiş ve ikinci aşama başlatılır. İkinci aşama, her görevin bu noktada oluşturulan tüm verilere erişmesini gerektirdiğinden, engeli gereklidir. Engel olmadan, tamamlanacak ilk görevler henüz başka görevler tarafından doldurulmamış olan arabelleklerden okumayı deneyebilir. Herhangi bir sayıda aşamayı bu şekilde eşzamanlı hale getirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
