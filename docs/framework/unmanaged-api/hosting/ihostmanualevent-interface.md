---
title: IHostManualEvent Arabirimi
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208637"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="43a89-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a89-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="43a89-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="43a89-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43a89-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="43a89-104">Methods</span></span>  
  
|<span data-ttu-id="43a89-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="43a89-105">Method</span></span>|<span data-ttu-id="43a89-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43a89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43a89-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43a89-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="43a89-108">Geçerli sıfırlar `IHostManualEvent` verilmemiş bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="43a89-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="43a89-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43a89-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="43a89-110">Geçerli ayarlar `IHostManualEvent` sinyal verilmiş duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="43a89-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="43a89-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43a89-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="43a89-112">Geçerli neden `IHostManualEvent` ait kadar beklenecek örneği veya belirli bir zaman geçtikçe miktarını.</span><span class="sxs-lookup"><span data-stu-id="43a89-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43a89-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43a89-113">Requirements</span></span>  
 <span data-ttu-id="43a89-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43a89-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43a89-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43a89-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43a89-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="43a89-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="43a89-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="43a89-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43a89-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43a89-118">See also</span></span>

- [<span data-ttu-id="43a89-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a89-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="43a89-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a89-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="43a89-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a89-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="43a89-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a89-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="43a89-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43a89-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
