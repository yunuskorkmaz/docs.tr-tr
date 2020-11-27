---
title: Örnekler
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: f4bf639e626945c7e753ac352dfecc7a79541bfd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266083"
---
# <a name="instances"></a><span data-ttu-id="51f9a-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="51f9a-102">Instances</span></span>

<span data-ttu-id="51f9a-103">Sayaç adı: örnekler.</span><span class="sxs-lookup"><span data-stu-id="51f9a-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="51f9a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f9a-104">Description</span></span>  

 <span data-ttu-id="51f9a-105">Hizmetin Şu anda içerdiği örnek bağlamların sayısı.</span><span class="sxs-lookup"><span data-stu-id="51f9a-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="51f9a-106">Çoğu zaman, örnek bağlamların sayısı örneklerin sayısıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="51f9a-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="51f9a-107">Ancak, aşağıdaki senaryolar bu kural için özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="51f9a-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="51f9a-108">Bir hizmet yöntemi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça çağırır.</span><span class="sxs-lookup"><span data-stu-id="51f9a-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="51f9a-109">Bir <xref:System.ServiceModel.ReleaseInstanceMode> <xref:System.ServiceModel.OperationBehaviorAttribute> örneğe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51f9a-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f9a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f9a-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
