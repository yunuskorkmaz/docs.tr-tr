---
description: 'Daha fazla bilgi edinin: IHostTask arabirimi'
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
ms.openlocfilehash: c46bbdd2e881c20d1ffd634bec8ddfa3b70b0f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784671"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="d89a9-103">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a9-103">IHostTask Interface</span></span>

<span data-ttu-id="d89a9-104">Ortak dil çalışma zamanının (CLR) görevleri yönetmek için konakla iletişim kurmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d89a9-104">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d89a9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d89a9-105">Methods</span></span>  
  
|<span data-ttu-id="d89a9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d89a9-106">Method</span></span>|<span data-ttu-id="d89a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d89a9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d89a9-108">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-108">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="d89a9-109">Konağın geçerli örnek tarafından temsil ettiği görevi `IHostTask` uyandırmasını, bu nedenle görevin iptal edileceğini ister.</span><span class="sxs-lookup"><span data-stu-id="d89a9-109">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="d89a9-110">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-110">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="d89a9-111">Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="d89a9-111">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d89a9-112">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-112">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="d89a9-113">Geçerli örnek tarafından temsil edilen görev `IHostTask` tamamlanana kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](ihosttask-alert-method.md) çağrıldığında çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="d89a9-113">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="d89a9-114">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-114">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="d89a9-115">Bir [ICLRTask arabirimi](iclrtask-interface.md) örneğini geçerli `IHostTask` örnekle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d89a9-115">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d89a9-116">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-116">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="d89a9-117">Konağın, geçerli örnek tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="d89a9-117">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="d89a9-118">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a9-118">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="d89a9-119">Konağın geçerli örnek tarafından temsil edilen görevi `IHostTask` askıya alınmış bir durumdan canlı duruma taşımasını ister, bu da kodun yürütülebileceğini.</span><span class="sxs-lookup"><span data-stu-id="d89a9-119">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d89a9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d89a9-120">Remarks</span></span>  

 <span data-ttu-id="d89a9-121">CLR, `IHostTask` bir görevi başlatmak, iş parçacığı öncelik düzeyini ayarlamak ve daha fazlasını yapmak için tarafından tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="d89a9-121">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89a9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d89a9-122">Requirements</span></span>  

 <span data-ttu-id="d89a9-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d89a9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89a9-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d89a9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d89a9-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d89a9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d89a9-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89a9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89a9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d89a9-127">See also</span></span>

- [<span data-ttu-id="d89a9-128">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a9-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d89a9-129">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a9-129">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d89a9-130">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a9-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="d89a9-131">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d89a9-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
