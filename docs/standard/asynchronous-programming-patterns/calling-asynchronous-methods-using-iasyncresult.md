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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ab98973fadf1893b4954fd19f679fe0ff690539d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="1a14e-102">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma </span><span class="sxs-lookup"><span data-stu-id="1a14e-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="1a14e-103">.NET Framework ve üçüncü taraf sınıf kitaplıkları türleri ana uygulama iş parçacığı dışında iş parçacıklarında zaman uyumsuz işlemleri gerçekleştirirken yürütme devam etmek uygulama izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a14e-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="1a14e-104">Aşağıdaki bölümlerde açıklar ve zaman uyumsuz yöntem çağrısı farklı yolları gösteren kod örnekleri sağlayın <xref:System.IAsyncResult> tasarım deseni.</span><span class="sxs-lookup"><span data-stu-id="1a14e-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="1a14e-105">[Zaman uyumsuz bir işlemi sonlandırarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1a14e-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="1a14e-106">[Bir AsyncWaitHandle kullanarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="1a14e-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="1a14e-107">[Zaman uyumsuz bir işlem durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1a14e-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="1a14e-108">[Zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1a14e-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a14e-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a14e-109">See Also</span></span>  
 [<span data-ttu-id="1a14e-110">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="1a14e-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="1a14e-111">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a14e-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
