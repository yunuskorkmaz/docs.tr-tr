---
title: IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830460"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="ba183-102">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="ba183-102">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="ba183-103">.NET kitaplıkları ve üçüncü taraf sınıf kitaplıklarındaki türler, bir uygulamanın ana uygulama iş parçacığı dışındaki iş parçacıklarında zaman uyumsuz işlemler gerçekleştirirken yürütmeye devam etmesine izin veren yöntemler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ba183-103">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="ba183-104">Aşağıdaki bölümlerde, tasarım modelini kullanan zaman uyumsuz yöntemleri çağırabileceğiniz farklı yolları gösteren kod örnekleri açıklanır ve sağlanmıştır <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="ba183-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="ba183-105">[Zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ba183-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="ba183-106">[AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="ba183-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="ba183-107">[Zaman uyumsuz bir Işlemin durumu yoklanıyor](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ba183-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="ba183-108">[Zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ba183-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba183-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba183-109">See also</span></span>

- [<span data-ttu-id="ba183-110">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="ba183-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="ba183-111">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ba183-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
