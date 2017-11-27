---
title: "IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81c05aeae00e79f614ef1514e54765b21e7e2dde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="7a470-102">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma </span><span class="sxs-lookup"><span data-stu-id="7a470-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="7a470-103">.NET Framework ve üçüncü taraf sınıf kitaplıkları türleri ana uygulama iş parçacığı dışında iş parçacıklarında zaman uyumsuz işlemleri gerçekleştirirken yürütme devam etmek uygulama izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a470-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="7a470-104">Aşağıdaki bölümlerde açıklar ve zaman uyumsuz yöntem çağrısı farklı yolları gösteren kod örnekleri sağlayın <xref:System.IAsyncResult> tasarım deseni.</span><span class="sxs-lookup"><span data-stu-id="7a470-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="7a470-105">[Zaman uyumsuz bir işlemi sonlandırarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7a470-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="7a470-106">[Bir AsyncWaitHandle kullanarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="7a470-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="7a470-107">[Zaman uyumsuz bir işlem durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7a470-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="7a470-108">[Zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7a470-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a470-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a470-109">See Also</span></span>  
 [<span data-ttu-id="7a470-110">Olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="7a470-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="7a470-111">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="7a470-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
