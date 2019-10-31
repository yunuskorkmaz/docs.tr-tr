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
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136789"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="61377-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61377-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="61377-103">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="61377-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61377-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="61377-104">Methods</span></span>  
  
|<span data-ttu-id="61377-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="61377-105">Method</span></span>|<span data-ttu-id="61377-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61377-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61377-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61377-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="61377-108">Geçerli `IHostManualEvent` örneğini, sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="61377-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="61377-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61377-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="61377-110">Geçerli `IHostManualEvent` örneğini bir sinyal durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61377-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="61377-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61377-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="61377-112">Geçerli `IHostManualEvent` örneğinin, ait olana veya belirli bir süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="61377-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61377-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61377-113">Requirements</span></span>  
 <span data-ttu-id="61377-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61377-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61377-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61377-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61377-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="61377-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61377-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61377-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61377-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61377-118">See also</span></span>

- [<span data-ttu-id="61377-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61377-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="61377-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61377-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="61377-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61377-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="61377-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61377-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="61377-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="61377-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
