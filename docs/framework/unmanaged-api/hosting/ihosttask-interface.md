---
title: IHostTask Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a><span data-ttu-id="6e0b8-102">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-102">IHostTask Interface</span></span>
<span data-ttu-id="6e0b8-103">Ortak dil çalışma zamanı (CLR) görevleri yönetmek için konak ile iletişim kurmasına izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e0b8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e0b8-104">Methods</span></span>  
  
|<span data-ttu-id="6e0b8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e0b8-105">Method</span></span>|<span data-ttu-id="6e0b8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e0b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e0b8-107">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="6e0b8-108">Ana bilgisayar tarafından geçerli temsil görev Uyandırma isteklerini `IHostTask` görevi durduruldu şekilde örneği.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="6e0b8-109">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="6e0b8-110">Geçerli tarafından temsil edilen görev iş parçacığı öncelik düzeyini alır `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="6e0b8-111">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="6e0b8-112">Geçerli tarafından temsil edilen görev kadar arama görev engeller `IHostTask` örneği tamamlandıktan, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="6e0b8-113">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="6e0b8-114">İlişkilendiren bir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) geçerli örnekle `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="6e0b8-115">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="6e0b8-116">Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen görev `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="6e0b8-117">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="6e0b8-118">Taşıma geçerli tarafından temsil edilen görevi konak istekleri `IHostTask` askıya alınma durumundaysa bir örnekten, kod yürütülebilir canlı bir duruma.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e0b8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e0b8-119">Remarks</span></span>  
 <span data-ttu-id="6e0b8-120">CLR tarafından tanımlanan yöntemlerini çağıran `IHostTask` iş parçacığı önceliği bir görevi başlatmak için level vb. ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e0b8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e0b8-121">Requirements</span></span>  
 <span data-ttu-id="6e0b8-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e0b8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e0b8-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e0b8-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e0b8-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6e0b8-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e0b8-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e0b8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e0b8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e0b8-126">See Also</span></span>  
 [<span data-ttu-id="6e0b8-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6e0b8-128">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6e0b8-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e0b8-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="6e0b8-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e0b8-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
