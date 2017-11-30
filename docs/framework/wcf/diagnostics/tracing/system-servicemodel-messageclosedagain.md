---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3963fe28ccaf55b3946254e395b770619c8f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="7dca1-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="7dca1-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="7dca1-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="7dca1-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="7dca1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dca1-104">Description</span></span>  
 <span data-ttu-id="7dca1-105">Bir ileti yeniden kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="7dca1-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="7dca1-106">Bir ileti yalnızca bir kez kapatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="7dca1-106">A message should be closed only once.</span></span> <span data-ttu-id="7dca1-107">Bu izleme kullanıcı uzantısı kodunda yayılan, kullanıcı uzantı kodu zaten kapatılmış bir ileti kapatılıyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="7dca1-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="7dca1-108">Bu izleme ürün kodu yayılan, kullanıcı uzantı kodu potansiyel olarak bir ileti çok erken kapatma olması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7dca1-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dca1-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dca1-109">See Also</span></span>  
 [<span data-ttu-id="7dca1-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="7dca1-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7dca1-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="7dca1-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7dca1-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="7dca1-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
