---
title: Örnekler
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473048"
---
# <a name="instances"></a><span data-ttu-id="6735f-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6735f-102">Instances</span></span>
<span data-ttu-id="6735f-103">Sayaç adı: örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6735f-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6735f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6735f-104">Description</span></span>  
 <span data-ttu-id="6735f-105">Hizmet şu anda içeren örneği bağlamları sayısı.</span><span class="sxs-lookup"><span data-stu-id="6735f-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="6735f-106">Çoğu zaman, örnek bağlamları sayısı örnek sayısı için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6735f-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="6735f-107">Ancak, aşağıdaki senaryolar bu kural için özel değildir.</span><span class="sxs-lookup"><span data-stu-id="6735f-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="6735f-108">Bir hizmet yöntemini çağıran <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="6735f-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="6735f-109">A <xref:System.ServiceModel.ReleaseInstanceMode> uygulanan bir <xref:System.ServiceModel.OperationBehaviorAttribute> örneği.</span><span class="sxs-lookup"><span data-stu-id="6735f-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6735f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6735f-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
