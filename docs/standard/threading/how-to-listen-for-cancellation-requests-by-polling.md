---
title: 'Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1794b47db87f636cc2ccdf2eecb9e7ca334ae659
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181398"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme
Aşağıdaki örnek, kullanıcı kodu çağıran iş parçacığından iptal isteğinde olup olmadığını görmek için düzenli aralıklarla bir iptal belirteci yoklama yollarından biri gösterilmektedir. Bu örnekte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü, ancak aynı düzeni uygular doğrudan tarafından oluşturulan zaman uyumsuz işlemler için <xref:System.Threading.ThreadPool?displayProperty=nameWithType> türü veya <xref:System.Threading.Thread?displayProperty=nameWithType> türü.  
  
## <a name="example"></a>Örnek  
 Yoklama gerektiren bazı türde bir Boolean değeri düzenli aralıklarla okuyabilirsiniz döngü veya yinelenen kod <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği. Kullanıyorsanız <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü ve, olan görev çağıran iş parçacığında tamamlanması için bekleme, kullanabileceğiniz <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> özelliğini denetleyin ve özel durum için yöntem. Bu yöntemi kullanarak bir isteğine yanıt olarak doğru özel durumun emin olun. Kullanıyorsanız bir <xref:System.Threading.Tasks.Task>, bu yöntemin çağrılması el ile oluşturma daha iyi ise bir <xref:System.OperationCanceledException>. Özel durum gerekmez sonra yalnızca özelliğini denetleyin ve özellik ise yöntemden dönüş `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Çağırma <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> son derece hızlı ve Döngülerde önemli ölçüde sunmaz.  
  
 Çağırıyorsanız <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, yalnızca açıkça denetlemek sahip <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> yanıt olarak iptal özel durumu oluşturan yanı sıra yapacak başka işleri varsa özelliği. Bu örnekte, kod gerçekten özelliği iki kez erişimi olduğunu görebilirsiniz: bir kez açık erişim ve yeniden <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi. Ancak okuma işlemi <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği yalnızca bir geçici okuma erişimi başına yönerge içerir, çift erişim performans açısından önemli değildir. Yöntemini çağırmak yerine, el ile throw için tercih edilir <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
