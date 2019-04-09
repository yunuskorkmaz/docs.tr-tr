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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081508"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="d63bf-102">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d63bf-102">IHostTask Interface</span></span>
<span data-ttu-id="d63bf-103">Ortak dil çalışma zamanı (CLR) görevleri yönetmek için ana bilgisayarı ile iletişim kurmasına izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d63bf-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d63bf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d63bf-104">Methods</span></span>  
  
|<span data-ttu-id="d63bf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d63bf-105">Method</span></span>|<span data-ttu-id="d63bf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d63bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d63bf-107">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="d63bf-108">Ana bilgisayar geçerli tarafından temsil edilen bir görev Uyandırma isteklerini `IHostTask` görev iptal için örnek.</span><span class="sxs-lookup"><span data-stu-id="d63bf-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="d63bf-109">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="d63bf-110">İş parçacığı öncelik düzeyi geçerli tarafından temsil edilen bir görev alır `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="d63bf-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d63bf-111">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="d63bf-112">Geçerli tarafından temsil edilen bir görev kadar çağırma göreviyle engeller `IHostTask` örneği tamamlanana, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d63bf-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="d63bf-113">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="d63bf-114">İlişkilendirir bir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) geçerli örnekle `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="d63bf-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d63bf-115">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="d63bf-116">Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen bir görev `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="d63bf-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d63bf-117">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d63bf-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="d63bf-118">Ana bilgisayar geçerli tarafından temsil edilen görevi taşıma istekler `IHostTask` askıya alınma durumuna örneğinden Canlı durumuna, hangi kod yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="d63bf-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d63bf-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d63bf-119">Remarks</span></span>  
 <span data-ttu-id="d63bf-120">CLR tarafından tanımlanan yöntemlerini çağıran `IHostTask` iş parçacığı önceliği bir görevi başlatmak için düzeyi, vb. ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d63bf-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d63bf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d63bf-121">Requirements</span></span>  
 <span data-ttu-id="d63bf-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d63bf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d63bf-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d63bf-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d63bf-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d63bf-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d63bf-125">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d63bf-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d63bf-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d63bf-126">See also</span></span>

- [<span data-ttu-id="d63bf-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d63bf-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d63bf-128">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d63bf-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d63bf-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d63bf-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="d63bf-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d63bf-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
