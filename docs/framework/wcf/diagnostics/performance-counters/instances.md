---
title: "Örnekler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87423c3de551cb9fbf8c5a7756e2f0f999129a3b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="instances"></a><span data-ttu-id="732c0-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="732c0-102">Instances</span></span>
<span data-ttu-id="732c0-103">Sayaç adı: örnekleri.</span><span class="sxs-lookup"><span data-stu-id="732c0-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="732c0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="732c0-104">Description</span></span>  
 <span data-ttu-id="732c0-105">Hizmet şu anda içeren örneği bağlamları sayısı.</span><span class="sxs-lookup"><span data-stu-id="732c0-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="732c0-106">Çoğu zaman, örnek bağlamları sayısı örnek sayısı için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="732c0-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="732c0-107">Ancak, aşağıdaki senaryolar bu kural için özel değildir.</span><span class="sxs-lookup"><span data-stu-id="732c0-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="732c0-108">Bir hizmet yöntemini çağıran <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="732c0-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="732c0-109">A <xref:System.ServiceModel.ReleaseInstanceMode> uygulanan bir <xref:System.ServiceModel.OperationBehaviorAttribute> örneği.</span><span class="sxs-lookup"><span data-stu-id="732c0-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732c0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="732c0-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
