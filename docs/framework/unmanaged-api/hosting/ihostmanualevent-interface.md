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
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438762"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="fe844-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe844-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="fe844-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe844-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe844-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe844-104">Methods</span></span>  
  
|<span data-ttu-id="fe844-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe844-105">Method</span></span>|<span data-ttu-id="fe844-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe844-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe844-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe844-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="fe844-108">Geçerli sıfırlar `IHostManualEvent` işaret olmayan bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="fe844-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="fe844-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe844-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="fe844-110">Geçerli ayarlar `IHostManualEvent` iş durumuna örneği.</span><span class="sxs-lookup"><span data-stu-id="fe844-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="fe844-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe844-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="fe844-112">Geçerli neden `IHostManualEvent` örneği ait kadar bekleyin veya belirli bir süre geçtikten miktarını.</span><span class="sxs-lookup"><span data-stu-id="fe844-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe844-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe844-113">Requirements</span></span>  
 <span data-ttu-id="fe844-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe844-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe844-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe844-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe844-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe844-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe844-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe844-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe844-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe844-118">See Also</span></span>  
 [<span data-ttu-id="fe844-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe844-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="fe844-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe844-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="fe844-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe844-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="fe844-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe844-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="fe844-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe844-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
