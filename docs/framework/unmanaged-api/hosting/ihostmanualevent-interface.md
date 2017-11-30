---
title: IHostManualEvent Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c19125d96d5f4a9e91fc083d53f36ebebd2c569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="27698-102">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27698-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="27698-103">Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="27698-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27698-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="27698-104">Methods</span></span>  
  
|<span data-ttu-id="27698-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="27698-105">Method</span></span>|<span data-ttu-id="27698-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27698-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27698-107">Reset yöntemi</span><span class="sxs-lookup"><span data-stu-id="27698-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="27698-108">Geçerli sıfırlar `IHostManualEvent` işaret olmayan bir duruma örneği.</span><span class="sxs-lookup"><span data-stu-id="27698-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="27698-109">Set yöntemi</span><span class="sxs-lookup"><span data-stu-id="27698-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="27698-110">Geçerli ayarlar `IHostManualEvent` iş durumuna örneği.</span><span class="sxs-lookup"><span data-stu-id="27698-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="27698-111">Wait yöntemi</span><span class="sxs-lookup"><span data-stu-id="27698-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="27698-112">Geçerli neden `IHostManualEvent` örneği ait kadar bekleyin veya belirli bir süre geçtikten miktarını.</span><span class="sxs-lookup"><span data-stu-id="27698-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27698-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27698-113">Requirements</span></span>  
 <span data-ttu-id="27698-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27698-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27698-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27698-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27698-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="27698-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27698-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27698-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27698-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27698-118">See Also</span></span>  
 [<span data-ttu-id="27698-119">Iclrsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="27698-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="27698-120">Ihostautoevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="27698-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="27698-121">Ihostsemaphore arabirimi</span><span class="sxs-lookup"><span data-stu-id="27698-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="27698-122">Ihostsyncmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="27698-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="27698-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27698-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
