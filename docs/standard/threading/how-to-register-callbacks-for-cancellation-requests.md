---
title: İptal istekleri için geri çağırmaları Kaydet
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608459"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="36ef8-102">İptal istekleri için geri çağırmaları Kaydet</span><span class="sxs-lookup"><span data-stu-id="36ef8-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="36ef8-103">Bir özellik doğru olduğunda çağrılacak bir temsilciyi nasıl kaydedeceğinizi öğrenin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> .</span><span class="sxs-lookup"><span data-stu-id="36ef8-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="36ef8-104">Belirteci oluşturan nesne üzerinde yapılan bir çağrı yapıldığında değer false olarak değişir <xref:System.Threading.CancellationTokenSource.Cancel%2A> .</span><span class="sxs-lookup"><span data-stu-id="36ef8-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="36ef8-105">Birleşik iptal çerçevesini yerel olarak desteklemeyen ve zaman uyumsuz bir işlemin tamamlanmasını bekleyen yöntemlerin engellemesini kaldırma işlemlerinde bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="36ef8-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="36ef8-106">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36ef8-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="36ef8-107">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="36ef8-107">This error is benign.</span></span> <span data-ttu-id="36ef8-108"><kbd>F5</kbd> tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36ef8-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="36ef8-109">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="36ef8-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="36ef8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ef8-110">Example</span></span>

<span data-ttu-id="36ef8-111">Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci aracılığıyla iptal istendiğinde çağrılacak yöntem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="36ef8-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="36ef8-112">Geri çağırma kaydedildiğinde iptal işlemi zaten isteniyorsa, geri aramanın çağrılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="36ef8-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="36ef8-113">Bu durumda, <xref:System.Net.WebClient.CancelAsync%2A> zaman uyumsuz bir işlem devam ederken yöntem hiçbir şey yapmaz, bu nedenle yöntemi çağırmak her zaman güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="36ef8-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="36ef8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ef8-114">See also</span></span>

- [<span data-ttu-id="36ef8-115">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="36ef8-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
