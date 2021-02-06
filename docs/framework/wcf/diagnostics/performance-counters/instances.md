---
description: 'Daha fazla bilgi edinin: örnekler'
title: Örnekler
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 9cd602164816a419b481ff600a7537593d4f500e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655272"
---
# <a name="instances"></a><span data-ttu-id="e401f-103">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e401f-103">Instances</span></span>

<span data-ttu-id="e401f-104">Sayaç adı: örnekler.</span><span class="sxs-lookup"><span data-stu-id="e401f-104">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e401f-105">Description</span><span class="sxs-lookup"><span data-stu-id="e401f-105">Description</span></span>  

 <span data-ttu-id="e401f-106">Hizmetin Şu anda içerdiği örnek bağlamların sayısı.</span><span class="sxs-lookup"><span data-stu-id="e401f-106">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="e401f-107">Çoğu zaman, örnek bağlamların sayısı örneklerin sayısıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e401f-107">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="e401f-108">Ancak, aşağıdaki senaryolar bu kural için özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="e401f-108">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="e401f-109">Bir hizmet yöntemi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça çağırır.</span><span class="sxs-lookup"><span data-stu-id="e401f-109">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="e401f-110">Bir <xref:System.ServiceModel.ReleaseInstanceMode> <xref:System.ServiceModel.OperationBehaviorAttribute> örneğe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e401f-110">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e401f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e401f-111">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
