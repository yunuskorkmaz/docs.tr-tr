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
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442227"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="c1a77-102">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a77-102">IHostTask Interface</span></span>
<span data-ttu-id="c1a77-103">Ortak dil çalışma zamanı (CLR) görevleri yönetmek için konak ile iletişim kurmasına izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a77-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1a77-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1a77-104">Methods</span></span>  
  
|<span data-ttu-id="c1a77-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c1a77-105">Method</span></span>|<span data-ttu-id="c1a77-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1a77-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1a77-107">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="c1a77-108">Ana bilgisayar tarafından geçerli temsil görev Uyandırma isteklerini `IHostTask` görevi durduruldu şekilde örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a77-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="c1a77-109">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="c1a77-110">Geçerli tarafından temsil edilen görev iş parçacığı öncelik düzeyini alır `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a77-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="c1a77-111">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="c1a77-112">Geçerli tarafından temsil edilen görev kadar arama görev engeller `IHostTask` örneği tamamlandıktan, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c1a77-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="c1a77-113">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="c1a77-114">İlişkilendiren bir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) geçerli örnekle `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a77-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="c1a77-115">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="c1a77-116">Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen görev `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a77-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="c1a77-117">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a77-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="c1a77-118">Taşıma geçerli tarafından temsil edilen görevi konak istekleri `IHostTask` askıya alınma durumundaysa bir örnekten, kod yürütülebilir canlı bir duruma.</span><span class="sxs-lookup"><span data-stu-id="c1a77-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a77-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1a77-119">Remarks</span></span>  
 <span data-ttu-id="c1a77-120">CLR tarafından tanımlanan yöntemlerini çağıran `IHostTask` iş parçacığı önceliği bir görevi başlatmak için level vb. ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1a77-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a77-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a77-121">Requirements</span></span>  
 <span data-ttu-id="c1a77-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a77-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a77-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1a77-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1a77-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1a77-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1a77-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a77-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a77-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a77-126">See Also</span></span>  
 [<span data-ttu-id="c1a77-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a77-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1a77-128">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a77-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1a77-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a77-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="c1a77-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1a77-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
