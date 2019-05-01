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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd55bd62653ef64668c13eb791b10afd2013f5f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031986"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="a068a-102">Zaman Uyumsuz Bir İşlemin Durumu için Yoklama</span><span class="sxs-lookup"><span data-stu-id="a068a-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="a068a-103">Zaman uyumsuz bir işlemin sonuçları için beklenirken diğer işlerinizi yapabilirsiniz uygulamalar işlem tamamlanana kadar bekleyen Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="a068a-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="a068a-104">Bir zaman uyumsuz bir işlemin tamamlanması beklenirken yönergeleri yürütme devam etmek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a068a-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="a068a-105">Kullanım <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak**_OperationName_ işleminin tamamlanıp tamamlanmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a068a-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="a068a-106">Bu yaklaşım, yoklama olarak bilinir ve bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a068a-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="a068a-107">Kullanım bir <xref:System.AsyncCallback> zaman uyumsuz işlemin ayrı bir iş parçacığında sonuçları işlemek için temsilci.</span><span class="sxs-lookup"><span data-stu-id="a068a-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="a068a-108">Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="a068a-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a068a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a068a-109">Example</span></span>  
 <span data-ttu-id="a068a-110">Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> sınıfı, kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistemi bilgileri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="a068a-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="a068a-111">Bu örnekte, zaman uyumsuz işlemi başlatır ve ardından nokta yazdırır (".") işlemi tamamlanana kadar konsolda.</span><span class="sxs-lookup"><span data-stu-id="a068a-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="a068a-112">Unutmayın **null** (**hiçbir şey** Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> ve <xref:System.Object> parametreleri bu bağımsız değişkenler bu yaklaşım kullanırken gerekli olmadığından.</span><span class="sxs-lookup"><span data-stu-id="a068a-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a068a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a068a-113">See also</span></span>

- [<span data-ttu-id="a068a-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="a068a-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="a068a-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a068a-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
