---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9a456e668560cb2172de80295b731a6103aa7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="e9615-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="e9615-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="e9615-103">Bir düzenleyici listelemesi için durum makinesinin tamamlanmış duruma geçti.</span><span class="sxs-lookup"><span data-stu-id="e9615-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e9615-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9615-104">Description</span></span>  
 <span data-ttu-id="e9615-105">Yerel işlem yöneticisi üstün düzenleyici listelemesi 2pc işleme tamamlandı düşündüğü, izlenen.</span><span class="sxs-lookup"><span data-stu-id="e9615-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="e9615-106">Kaydı için sonuç, kabul edilen veya iptal edildi veya Forgotten olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9615-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="e9615-107">Yerel işlem yöneticisi salt okunur hazırlama sırasında oylarının, ayrıca izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="e9615-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9615-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9615-108">See Also</span></span>  
 [<span data-ttu-id="e9615-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="e9615-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e9615-110">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="e9615-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e9615-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="e9615-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
