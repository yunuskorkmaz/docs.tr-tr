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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="b2aa1-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b2aa1-102">Instances</span></span>
<span data-ttu-id="b2aa1-103">Sayaç adı: örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b2aa1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2aa1-104">Description</span></span>  
 <span data-ttu-id="b2aa1-105">Hizmet şu anda içeren örneği bağlamları sayısı.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="b2aa1-106">Çoğu zaman, örnek bağlamları sayısı örnek sayısı için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="b2aa1-107">Ancak, aşağıdaki senaryolar bu kural için özel değildir.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="b2aa1-108">Bir hizmet yöntemini çağıran <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="b2aa1-109">A <xref:System.ServiceModel.ReleaseInstanceMode> uygulanan bir <xref:System.ServiceModel.OperationBehaviorAttribute> örneği.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2aa1-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2aa1-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
