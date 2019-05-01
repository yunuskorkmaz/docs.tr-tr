---
title: Örnekler
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916402"
---
# <a name="instances"></a><span data-ttu-id="15b55-102">Örnekler</span><span class="sxs-lookup"><span data-stu-id="15b55-102">Instances</span></span>
<span data-ttu-id="15b55-103">Sayaç adı: örnekleri.</span><span class="sxs-lookup"><span data-stu-id="15b55-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15b55-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15b55-104">Description</span></span>  
 <span data-ttu-id="15b55-105">Hizmet şu anda içeren örnek bağlamları sayısı.</span><span class="sxs-lookup"><span data-stu-id="15b55-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="15b55-106">Çoğu zaman örneği bağlamları sayısını örnek sayısı için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="15b55-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="15b55-107">Ancak, aşağıdaki senaryolarda bu kuralın istisnası olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="15b55-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="15b55-108">Bir hizmet yöntemini çağırır <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="15b55-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="15b55-109">A <xref:System.ServiceModel.ReleaseInstanceMode> uygulanan bir <xref:System.ServiceModel.OperationBehaviorAttribute> örneği.</span><span class="sxs-lookup"><span data-stu-id="15b55-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b55-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15b55-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
