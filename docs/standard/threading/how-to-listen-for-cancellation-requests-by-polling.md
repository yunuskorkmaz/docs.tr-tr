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
ms.openlocfilehash: 6f70ce75b1d6a3d4d7e8a38d739005a261b07241
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279562"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme
Aşağıdaki örnek, kullanıcı kodunun, çağırma iş parçacığından İptalin istenip istenmediğini görmek için, düzenli aralıklarla bir iptal belirtecini yoklamasının bir yolunu gösterir. Bu örnek türünü kullanır <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> , ancak aynı model doğrudan <xref:System.Threading.ThreadPool?displayProperty=nameWithType> tür veya tür tarafından oluşturulan zaman uyumsuz işlemler için geçerlidir <xref:System.Threading.Thread?displayProperty=nameWithType> .  
  
## <a name="example"></a>Örnek  
 Yoklama, Boolean özelliğinin değerini düzenli aralıklarla okuyabilecekleri bazı tür döngü veya özyinelemeli kod gerektirir <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> . <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Türü kullanıyorsanız ve görevin çağıran iş parçacığında tamamlanmasını bekliyorsa, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> özelliği denetlemek ve özel durumu oluşturmak için yöntemini kullanabilirsiniz. Bu yöntemi kullanarak, bir isteğe yanıt olarak doğru özel durumun yapıldığından emin olursunuz. Kullanıyorsanız <xref:System.Threading.Tasks.Task> , bu yöntemi çağırmak el ile oluşturumaktan daha iyidir <xref:System.OperationCanceledException> . Özel durumu oluşturmak zorunda değilseniz, özelliği denetleyebilir ve özellik ise yönteminden geri dönebilirsiniz `true` .  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Çağırmak <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> son derece hızlıdır ve Döngülerde önemli bir ek yük sunmaz.  
  
 Öğesini arıyorsanız <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> , <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özel durumu oluşturma yanında iptal 'e yanıt olarak başka çalışmanız varsa, özelliği açıkça denetlemeniz gerekir. Bu örnekte, kodun özelliğe bir kez daha fazla kez eriştiğini görebilirsiniz: açık erişimde ve yöntemi içinde yeniden <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> . Ancak, özelliği okuma işlemi <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> erişim başına yalnızca bir geçici okuma yönergesi içerdiğinden, Çift erişim performans açısından önemli değildir. El ile oluşturmak yerine yöntemi çağırmak yine de tercih edilir <xref:System.OperationCanceledException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](cancellation-in-managed-threads.md)
