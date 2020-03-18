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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123968"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="2b7c5-102">Zaman Uyumsuz Bir İşlemin Durumu için Yoklama</span><span class="sxs-lookup"><span data-stu-id="2b7c5-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="2b7c5-103">Eşzamanlı işlemin sonuçlarını beklerken başka bir iş yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellememelidir.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="2b7c5-104">Eşzamanlı işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b7c5-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="2b7c5-105">İşlemin <xref:System.IAsyncResult.IsCompleted%2A> tamamlanıp <xref:System.IAsyncResult> tamamlanmadığını belirlemek için eşzamanlı işlemin **Begin**_OperationName_ yöntemi yle döndürülen özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="2b7c5-106">Bu yaklaşım yoklama olarak bilinir ve bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="2b7c5-107">Ayrı <xref:System.AsyncCallback> bir iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="2b7c5-108">Bu yaklaşımı gösteren bir örnek için [bkz.](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="2b7c5-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b7c5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b7c5-109">Example</span></span>  
 <span data-ttu-id="2b7c5-110">Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir <xref:System.Net.Dns> bilgisayar için Alan Adı Sistemi bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="2b7c5-111">Bu örnek, eşzamanlı işlemi başlatır ve işlem tamamlanana kadar konsolda dönemleri (".") yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="2b7c5-112">Bu yaklaşım kullanılırken bu bağımsız değişkenler <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> <xref:System.Object> gerekli olmadığından, **null** (Visual Basic hiçbir**şey)** ve parametreler için geçirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2b7c5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b7c5-113">See also</span></span>

- [<span data-ttu-id="2b7c5-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="2b7c5-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="2b7c5-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2b7c5-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
