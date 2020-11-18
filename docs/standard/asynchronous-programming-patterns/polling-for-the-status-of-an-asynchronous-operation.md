---
title: Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: c4e8e7c66551e0a240eaa873513c3975703af946
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830317"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="2df58-102">Zaman Uyumsuz Bir İşlemin Durumu için Yoklama</span><span class="sxs-lookup"><span data-stu-id="2df58-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="2df58-103">Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez.</span><span class="sxs-lookup"><span data-stu-id="2df58-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="2df58-104">Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2df58-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="2df58-105"><xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2df58-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="2df58-106">Bu yaklaşım yoklama olarak bilinir ve bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2df58-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="2df58-107"><xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullanın.</span><span class="sxs-lookup"><span data-stu-id="2df58-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="2df58-108">Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2df58-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2df58-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2df58-109">Example</span></span>  
 <span data-ttu-id="2df58-110">Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bir bilgisayar Için etki alanı adı sistem bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2df58-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="2df58-111">Bu örnek, zaman uyumsuz işlemi başlatır ve sonra işlem tamamlanana kadar konsola (".") nokta (".") yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2df58-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="2df58-112">**null** **Nothing** <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> <xref:System.Object> Bu yaklaşım kullanılırken bu bağımsız değişkenler gerekli olmadığından, ve parametreleri için null (Visual Basic hiçbir şey yok) geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2df58-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2df58-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2df58-113">See also</span></span>

- [<span data-ttu-id="2df58-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="2df58-114">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="2df58-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2df58-115">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
