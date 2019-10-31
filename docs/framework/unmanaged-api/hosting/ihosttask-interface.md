---
title: IHostTask Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121389"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="02e46-102">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02e46-102">IHostTask Interface</span></span>
<span data-ttu-id="02e46-103">Ortak dil çalışma zamanının (CLR) görevleri yönetmek için konakla iletişim kurmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02e46-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02e46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="02e46-104">Methods</span></span>  
  
|<span data-ttu-id="02e46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="02e46-105">Method</span></span>|<span data-ttu-id="02e46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02e46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02e46-107">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="02e46-108">Konağın geçerli `IHostTask` örneği tarafından temsil ettiği görevi uyandırmasını, dolayısıyla görevin iptal edileceğini ister.</span><span class="sxs-lookup"><span data-stu-id="02e46-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="02e46-109">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="02e46-110">Geçerli `IHostTask` örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="02e46-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="02e46-111">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="02e46-112">Geçerli `IHostTask` örneği tarafından temsil edilen görev tamamlanana kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrıldığında, çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="02e46-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="02e46-113">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="02e46-114">Bir [ICLRTask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini geçerli `IHostTask` örneğiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="02e46-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="02e46-115">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="02e46-116">Konağın geçerli `IHostTask` örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.</span><span class="sxs-lookup"><span data-stu-id="02e46-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="02e46-117">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02e46-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="02e46-118">Konağın geçerli `IHostTask` örneği tarafından temsil edilen görevi askıya alınmış bir durumdan canlı duruma taşımasını ister, bu da kodun yürütülebileceğini.</span><span class="sxs-lookup"><span data-stu-id="02e46-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02e46-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02e46-119">Remarks</span></span>  
 <span data-ttu-id="02e46-120">CLR, bir görevi başlatmak, iş parçacığı öncelik düzeyini ayarlamak ve bu şekilde `IHostTask` tarafından tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="02e46-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e46-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02e46-121">Requirements</span></span>  
 <span data-ttu-id="02e46-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02e46-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e46-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="02e46-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02e46-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="02e46-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02e46-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e46-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e46-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02e46-126">See also</span></span>

- [<span data-ttu-id="02e46-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02e46-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="02e46-128">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02e46-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="02e46-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02e46-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="02e46-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="02e46-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
