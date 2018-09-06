---
title: 'Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2d61ba254a76235a12ca5dda23fdecb8838ae75
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863588"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="db9ad-102">Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="db9ad-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="db9ad-103">Aşağıdaki örnek, olacak bir temsilci kaydettirmek gösterilmektedir ne zaman çağrılır bir <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özellik için bir çağrı nedeniyle true olur <xref:System.Threading.CancellationTokenSource.Cancel%2A> belirteç oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="db9ad-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="db9ad-104">Zaman uyumsuz bir işlemin tamamlanmasını bekleyen engellemeyi kaldırma yöntemleri yanı sıra, birleşik iptalini çerçevesi yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal etmek için bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="db9ad-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db9ad-105">"Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="db9ad-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="db9ad-106">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="db9ad-106">This error is benign.</span></span> <span data-ttu-id="db9ad-107">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="db9ad-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="db9ad-108">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="db9ad-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9ad-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="db9ad-109">Example</span></span>  
 <span data-ttu-id="db9ad-110">Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci İptal istendiğinde çağrılacak yöntem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="db9ad-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="db9ad-111">Geri çağırma kaydedildiğinde, zaten iptal istendi, geri çağırma çağrılacak yine de garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="db9ad-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="db9ad-112">Bu özel durumda <xref:System.Net.WebClient.CancelAsync%2A> yöntemi yaparsanız hiçbir şey her zaman güvenli bir yöntem çağırmak, bu nedenle hiçbir zaman uyumsuz bir işlem devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="db9ad-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9ad-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db9ad-113">See also</span></span>

- [<span data-ttu-id="db9ad-114">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="db9ad-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
