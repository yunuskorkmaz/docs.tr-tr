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
ms.openlocfilehash: df76674e3003bbb77ef062e90b1dc3283f681d35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138019"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme
Aşağıdaki örnek, kullanıcı kodunun, çağırma iş parçacığından İptalin istenip istenmediğini görmek için, düzenli aralıklarla bir iptal belirtecini yoklamasının bir yolunu gösterir. Bu örnek <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türünü kullanır, ancak aynı model doğrudan <xref:System.Threading.ThreadPool?displayProperty=nameWithType> türü veya <xref:System.Threading.Thread?displayProperty=nameWithType> türü tarafından oluşturulan zaman uyumsuz işlemler için geçerlidir.  
  
## <a name="example"></a>Örnek  
 Yoklama, Boole <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğinin değerini düzenli aralıklarla okuyabilecekleri bazı tür döngü veya özyinelemeli kod gerektirir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türünü kullanıyorsanız ve görevin çağıran iş parçacığında tamamlanmasını bekliyorsa, özelliği denetlemek ve özel durumu oluşturmak için <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemini kullanabilirsiniz. Bu yöntemi kullanarak, bir isteğe yanıt olarak doğru özel durumun yapıldığından emin olursunuz. <xref:System.Threading.Tasks.Task>kullanıyorsanız, bu yöntemi çağırmak <xref:System.OperationCanceledException>el ile oluşturmaktan daha iyidir. Özel durumu oluşturmak zorunda değilseniz, özelliği denetleyebilir ve özellik `true`ise yöntemden dönebilirsiniz.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> çağırmak son derece hızlıdır ve Döngülerde önemli bir ek yük sunmaz.  
  
 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>arıyorsanız, özel durumu oluşturma yanı sıra iptaline yanıt olarak başka çalışmanız varsa, yalnızca <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğini açıkça denetlemeniz gerekir. Bu örnekte, kodun özelliğe daha fazla kez eriştiğini görebilirsiniz: açık erişimde bir kez ve <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yönteminde tekrar. Ancak, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği okuma işlemi erişim başına yalnızca bir geçici okuma yönergesi içerdiğinden, Çift erişim performans açısından önemli değildir. <xref:System.OperationCanceledException>el ile oluşturmak yerine yöntemi çağırmak yine de tercih edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
