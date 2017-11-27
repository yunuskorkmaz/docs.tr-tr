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
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="04d58-102">Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="04d58-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="04d58-103">Aşağıdaki örnek olacak temsilci kaydedileceği gösterilmektedir olduğunda çağrılan bir <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özellik için bir çağrı nedeniyle true olur <xref:System.Threading.CancellationTokenSource.Cancel%2A> belirteç oluşturulan nesne üzerinde.</span><span class="sxs-lookup"><span data-stu-id="04d58-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="04d58-104">Bu teknik birleşik iptal framework yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal ediliyor ve tamamlamak için zaman uyumsuz bir işlemi bekliyor olabilir engellemesini kaldırma yöntemleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="04d58-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04d58-105">"Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir</span><span class="sxs-lookup"><span data-stu-id="04d58-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="04d58-106">Bu hata zararsız kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="04d58-106">This error is benign.</span></span> <span data-ttu-id="04d58-107">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın.</span><span class="sxs-lookup"><span data-stu-id="04d58-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="04d58-108">Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="04d58-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d58-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="04d58-109">Example</span></span>  
 <span data-ttu-id="04d58-110">Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci İptal istendiğinde çağrılacak yöntemi olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="04d58-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="04d58-111">Geri çağırma kaydedildikten sonra zaten iptal istendi, geri çağırma çağrılacak hala garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="04d58-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="04d58-112">Bu örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi yaparsanız hiçbir şey her zaman yöntemi çağırmak güvenli olması için hiçbir zaman uyumsuz işlemi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="04d58-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d58-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04d58-113">See Also</span></span>  
 [<span data-ttu-id="04d58-114">Yönetilen iş parçacıklarında iptal</span><span class="sxs-lookup"><span data-stu-id="04d58-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
