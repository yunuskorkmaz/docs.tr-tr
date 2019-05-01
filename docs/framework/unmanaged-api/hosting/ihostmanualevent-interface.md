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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973075"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="3e7b1-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="3e7b1-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e7b1-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e7b1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e7b1-104">Methods</span></span>  
  
|<span data-ttu-id="3e7b1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e7b1-105">Method</span></span>|<span data-ttu-id="3e7b1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e7b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e7b1-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="3e7b1-108">Geçerli sıfırlar `IHostManualEvent` verilmemiş bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="3e7b1-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="3e7b1-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="3e7b1-110">Geçerli ayarlar `IHostManualEvent` sinyal verilmiş duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="3e7b1-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="3e7b1-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="3e7b1-112">Geçerli neden `IHostManualEvent` ait kadar beklenecek örneği veya belirli bir zaman geçtikçe miktarını.</span><span class="sxs-lookup"><span data-stu-id="3e7b1-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e7b1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e7b1-113">Requirements</span></span>  
 <span data-ttu-id="3e7b1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7b1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7b1-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e7b1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e7b1-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3e7b1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e7b1-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e7b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7b1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e7b1-118">See also</span></span>

- [<span data-ttu-id="3e7b1-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3e7b1-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3e7b1-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="3e7b1-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e7b1-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="3e7b1-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3e7b1-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
