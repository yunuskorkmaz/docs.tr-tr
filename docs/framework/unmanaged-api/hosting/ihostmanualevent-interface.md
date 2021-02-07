---
description: 'Daha fazla bilgi edinin: IHostManualEvent Interface'
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
ms.openlocfilehash: 1c70935568b9ff4080fd5bcdc372c02d354aa06f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708170"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="cf790-103">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf790-103">IHostManualEvent Interface</span></span>

<span data-ttu-id="cf790-104">Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf790-104">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf790-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf790-105">Methods</span></span>  
  
|<span data-ttu-id="cf790-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cf790-106">Method</span></span>|<span data-ttu-id="cf790-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf790-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf790-108">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf790-108">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="cf790-109">Geçerli örneği, `IHostManualEvent` sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="cf790-109">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="cf790-110">Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf790-110">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="cf790-111">Geçerli `IHostManualEvent` örneği bir sinyal durumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf790-111">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="cf790-112">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf790-112">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="cf790-113">Geçerli örneğin, `IHostManualEvent` sahip olana kadar beklemesini veya belirli bir süre geçtikten sonra gelmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf790-113">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf790-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf790-114">Requirements</span></span>  

 <span data-ttu-id="cf790-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf790-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf790-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf790-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf790-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cf790-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf790-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf790-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf790-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf790-119">See also</span></span>

- [<span data-ttu-id="cf790-120">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf790-120">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="cf790-121">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf790-121">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="cf790-122">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf790-122">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="cf790-123">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf790-123">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="cf790-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf790-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
