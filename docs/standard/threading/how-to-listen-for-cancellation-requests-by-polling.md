---
title: "Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme"
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
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme
Aşağıdaki örnekte, kullanıcı kodu bir iptal belirteci iptal çağıran iş parçacığından istedi olup olmadığını görmek için düzenli aralıklarla yoklayabilir bir yolunu gösterir. Bu örnekte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü, ancak aynı düzeni uygular zaman uyumsuz işlemleri doğrudan tarafından oluşturulan <xref:System.Threading.ThreadPool?displayProperty=nameWithType> türü veya <xref:System.Threading.Thread?displayProperty=nameWithType> türü.  
  
## <a name="example"></a>Örnek  
 Yoklama gerektiren bazı tür düzenli aralıklarla Boolean değerini okuyabilirsiniz döngü veya özyinelemeli kodu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği. Kullanıyorsanız <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü ve görevinin çağıran iş parçacığında tamamlanmasını bekleyen, kullanabileceğiniz <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> özelliğini denetleyin ve özel durum için yöntem. Bu yöntemi kullanarak, doğru bir isteğe yanıt olarak özel durum emin olun. Kullanıyorsanız bir <xref:System.Threading.Tasks.Task>, sonra da bu yöntemi çağırmadan el ile atma daha iyi bir <xref:System.OperationCanceledException>. Özel durum gerekmez sonra yalnızca özelliğini denetleyin ve özellik ise döndürme `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Çağırma <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> son derece hızlı bir işlemdir ve döngüler önemli ek yükü sunmaz.  
  
 Aradığınız varsa <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, yalnızca açıkça denetlemek sahip <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> yanıt özel durum atma yanı sıra iptal olarak yapmak için diğer iş varsa, özelliği. Bu örnekte, kod gerçekte özelliği iki kez erişme görebilirsiniz: bir kez açık erişim ve yeniden <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi. Ancak çünkü okuma act <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği yalnızca bir geçici erişim başına yönerge okuma içerir, çift erişim performans açısından önemli değildir. El ile throw yöntemi çağırmak yerine hala tercih edilir <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
