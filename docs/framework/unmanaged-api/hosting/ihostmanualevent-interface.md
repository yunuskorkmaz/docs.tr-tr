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
ms.openlocfilehash: eb09422872a0d9565be286c25ca1b28d1c45e08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501704"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="d9aa7-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="d9aa7-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9aa7-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9aa7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d9aa7-104">Methods</span></span>  
  
|<span data-ttu-id="d9aa7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9aa7-105">Method</span></span>|<span data-ttu-id="d9aa7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9aa7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9aa7-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="d9aa7-108">Geçerli sıfırlar `IHostManualEvent` verilmemiş bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="d9aa7-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="d9aa7-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="d9aa7-110">Geçerli ayarlar `IHostManualEvent` sinyal verilmiş duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="d9aa7-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="d9aa7-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="d9aa7-112">Geçerli neden `IHostManualEvent` ait kadar beklenecek örneği veya belirli bir zaman geçtikçe miktarını.</span><span class="sxs-lookup"><span data-stu-id="d9aa7-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9aa7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9aa7-113">Requirements</span></span>  
 <span data-ttu-id="d9aa7-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9aa7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9aa7-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9aa7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9aa7-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d9aa7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9aa7-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9aa7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9aa7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9aa7-118">See also</span></span>
- [<span data-ttu-id="d9aa7-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d9aa7-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="d9aa7-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d9aa7-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9aa7-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="d9aa7-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d9aa7-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
