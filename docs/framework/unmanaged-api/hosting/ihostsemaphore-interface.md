---
description: 'Daha fazla bilgi edinin: ıhostsemafor arabirimi'
title: IHostSemaphore Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 682f1f70925310e93f88f1dc314052e801a5e87b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671368"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="d6f76-103">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6f76-103">IHostSemaphore Interface</span></span>

<span data-ttu-id="d6f76-104">Ana bilgisayarın iş parçacığı için semafor uygulamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6f76-104">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6f76-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d6f76-105">Methods</span></span>  
  
|<span data-ttu-id="d6f76-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d6f76-106">Method</span></span>|<span data-ttu-id="d6f76-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6f76-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6f76-108">ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6f76-108">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="d6f76-109">Geçerli `IHostSemaphore` Örneğin sayısını belirtilen miktarda artırır.</span><span class="sxs-lookup"><span data-stu-id="d6f76-109">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="d6f76-110">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6f76-110">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="d6f76-111">Geçerli örneğin, `IHostSemaphore` ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6f76-111">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6f76-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6f76-112">Requirements</span></span>  

 <span data-ttu-id="d6f76-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6f76-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f76-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6f76-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6f76-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d6f76-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6f76-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f76-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6f76-117">See also</span></span>

- [<span data-ttu-id="d6f76-118">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6f76-118">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d6f76-119">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6f76-119">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d6f76-120">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6f76-120">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d6f76-121">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6f76-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="d6f76-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6f76-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
