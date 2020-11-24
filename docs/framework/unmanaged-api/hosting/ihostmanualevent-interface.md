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
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673211"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="0c013-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c013-102">IHostManualEvent Interface</span></span>

<span data-ttu-id="0c013-103">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c013-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c013-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0c013-104">Methods</span></span>  
  
|<span data-ttu-id="0c013-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0c013-105">Method</span></span>|<span data-ttu-id="0c013-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c013-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c013-107">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c013-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="0c013-108">Geçerli örneği, `IHostManualEvent` sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="0c013-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="0c013-109">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c013-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="0c013-110">Geçerli `IHostManualEvent` örneği bir sinyal durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0c013-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="0c013-111">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c013-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="0c013-112">Geçerli örneğin, `IHostManualEvent` sahip olana kadar beklemesini veya belirli bir süre geçtikten sonra gelmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c013-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c013-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c013-113">Requirements</span></span>  

 <span data-ttu-id="0c013-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c013-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c013-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c013-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c013-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0c013-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c013-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c013-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c013-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c013-118">See also</span></span>

- [<span data-ttu-id="0c013-119">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c013-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0c013-120">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c013-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="0c013-121">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c013-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="0c013-122">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c013-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="0c013-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c013-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
