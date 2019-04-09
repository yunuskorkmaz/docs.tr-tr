---
title: Örnekler
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118995"
---
# <a name="instances"></a><span data-ttu-id="7660c-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7660c-102">Instances</span></span>
<span data-ttu-id="7660c-103">Sayaç adı: örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7660c-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7660c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7660c-104">Description</span></span>  
 <span data-ttu-id="7660c-105">Hizmet şu anda içeren örnek bağlamları sayısı.</span><span class="sxs-lookup"><span data-stu-id="7660c-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="7660c-106">Çoğu zaman örneği bağlamları sayısını örnek sayısı için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7660c-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="7660c-107">Ancak, aşağıdaki senaryolarda bu kuralın istisnası olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7660c-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="7660c-108">Bir hizmet yöntemini çağırır <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="7660c-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="7660c-109">A <xref:System.ServiceModel.ReleaseInstanceMode> uygulanan bir <xref:System.ServiceModel.OperationBehaviorAttribute> örneği.</span><span class="sxs-lookup"><span data-stu-id="7660c-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7660c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7660c-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
