---
title: 'IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma '
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121310"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="066c6-102">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma </span><span class="sxs-lookup"><span data-stu-id="066c6-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="066c6-103">.NET Framework ve üçüncü taraf sınıf kitaplıklarında kullanılan türler, ana uygulama iş parçacığı dışındaki iş parçacıklarında eşzamanlı işlemler gerçekleştirirken uygulamanın yürütmeye devam etmesine izin veren yöntemler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="066c6-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="066c6-104">Aşağıdaki bölümler, <xref:System.IAsyncResult> tasarım deseni kullanan eşzamanlı yöntemleri çağırabileceğiniz farklı yolları gösteren kod örneklerini açıklar ve sağlar.</span><span class="sxs-lookup"><span data-stu-id="066c6-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="066c6-105">[Bir Async İşlemini Sonlayarak Uygulama Yürütmeyi Engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="066c6-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="066c6-106">[AsyncWaitHandle kullanarak Uygulama Yürütme engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="066c6-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="066c6-107">[Bir Eşzamanlı İşlemin Durumu Için Yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="066c6-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="066c6-108">[Bir Eşzamanlı İşlemi Sona Erdirmek için Bir AsyncCallback Temsilcisi kullanma.](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="066c6-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066c6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="066c6-109">See also</span></span>

- [<span data-ttu-id="066c6-110">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="066c6-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="066c6-111">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="066c6-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
