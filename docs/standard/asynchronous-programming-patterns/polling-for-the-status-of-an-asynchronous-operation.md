---
title: Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123968"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="1c156-102">Zaman Uyumsuz Bir İşlemin Durumu için Yoklama</span><span class="sxs-lookup"><span data-stu-id="1c156-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="1c156-103">Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez.</span><span class="sxs-lookup"><span data-stu-id="1c156-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="1c156-104">Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="1c156-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="1c156-105">İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.IsCompleted%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c156-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="1c156-106">Bu yaklaşım yoklama olarak bilinir ve bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c156-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="1c156-107">Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir <xref:System.AsyncCallback> temsilcisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c156-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="1c156-108">Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1c156-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c156-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c156-109">Example</span></span>  
 <span data-ttu-id="1c156-110">Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistem bilgilerini almak üzere <xref:System.Net.Dns> sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c156-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="1c156-111">Bu örnek, zaman uyumsuz işlemi başlatır ve sonra işlem tamamlanana kadar konsola (".") nokta (".") yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1c156-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="1c156-112">Bu yaklaşım kullanılırken bu bağımsız değişkenler gerekmediği için, <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> ve <xref:System.Object> parametreleri için **null** (Visual Basic**hiçbir şey** ) geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1c156-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1c156-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c156-113">See also</span></span>

- [<span data-ttu-id="1c156-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="1c156-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="1c156-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c156-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
