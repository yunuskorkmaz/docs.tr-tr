---
title: "Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b71ebee3a28fb6a829edf657f56e54799097f351
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme
Aşağıdaki örnek olacak temsilci kaydedileceği gösterilmektedir olduğunda çağrılan bir <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özellik için bir çağrı nedeniyle true olur <xref:System.Threading.CancellationTokenSource.Cancel%2A> belirteç oluşturulan nesne üzerinde. Bu teknik birleşik iptal framework yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal ediliyor ve tamamlamak için zaman uyumsuz bir işlemi bekliyor olabilir engellemesini kaldırma yöntemleri için kullanın.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci İptal istendiğinde çağrılacak yöntemi olarak kaydedilir.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Geri çağırma kaydedildikten sonra zaten iptal istendi, geri çağırma çağrılacak hala garanti edilmez. Bu örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi yaparsanız hiçbir şey her zaman yöntemi çağırmak güvenli olması için hiçbir zaman uyumsuz işlemi devam ediyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
