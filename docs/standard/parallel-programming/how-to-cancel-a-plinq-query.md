---
title: "Nasıl yapılır: PLINQ Sorgusunu İptal Etme"
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
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunu İptal Etme
Aşağıdaki örnekler bir PLINQ sorgusunu iptal etmek için iki yol gösterir. İlk örnek çoğunlukla veri geçişi oluşan bir sorguyu iptal gösterilmektedir. İkinci örnek pkı'ya pahalıdır kullanıcı işlevi içeren bir sorguyu iptal etme gösterir.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
>   
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 Tek bir PLINQ framework döndürülmez <xref:System.OperationCanceledException> içine bir <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> ayrı catch bloğunda ele alınması gerekir. Bir veya daha fazla kullanıcı temsilcileri bir OperationCanceledException(externalCT) oluşturursa (bir dış kullanarak <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ancak başka bir özel durum ve sorgu olarak tanımlanmıştı `AsParallel().WithCancellation(externalCT)`, tek bir PLINQ verecek sonra <xref:System.OperationCanceledException> (externalCT) yerine bir <xref:System.AggregateException?displayProperty=nameWithType>. Ancak, bir kullanıcı temsilci döndürürse bir <xref:System.OperationCanceledException>ve başka bir özel durum türü başka bir temsilci oluşturur ve ardından her iki özel durumlar içine alınacak bir <xref:System.AggregateException>.  
  
 İptal genel yönergeler aşağıdaki gibidir:  
  
1.  Kullanıcı temsilci iptal gerçekleştirirseniz PLINQ dış hakkında bilgilendirmek <xref:System.Threading.CancellationToken> ve throw bir <xref:System.OperationCanceledException>(externalCT).  
  
2.  İptal gerçekleşir ve başka bir özel durum, daha sonra işlemesi gereken bir <xref:System.OperationCanceledException> yerine bir <xref:System.AggregateException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl pkı'ya pahalı bir işlev içinde kullanıcı kodu varsa, iptal işleneceğini gösterir.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Kullanıcı kodu iptal uyguluyorsanız kullanmak gerekmez <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu tanımı içinde. Ancak, çünkü bunu yapmanızı öneririz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi olmaz ve sorgu işleçleri ve kullanıcı kodu tarafından işlenecek iptal sağlar.  
  
 Sistem Yanıtlama Hızı emin olmak için İptal mili saniye başına bir kez çözmek için denetlemenizi öneririz; Bununla birlikte, 10 milisaniye kadar herhangi bir süre kabul edilebilir kabul edilir. Bu sıklık olumsuz etkiler, kodun performans üzerinde yok.  
  
 Bir numaralandırıcı olduğunda, örneğin, kod sorgu sonuçları yineleme bir (her biri için Visual Basic) foreach döngüsü dışında keser sonra sorgu iptal edildi, ancak hiçbir özel durum.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
