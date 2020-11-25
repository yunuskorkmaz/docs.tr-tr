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
ms.openlocfilehash: 10efe853c9a7ad7676058bc01b07063c557623d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699228"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="09392-102">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09392-102">IHostTask Interface</span></span>

<span data-ttu-id="09392-103">Ortak dil çalışma zamanının (CLR) görevleri yönetmek için konakla iletişim kurmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="09392-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09392-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09392-104">Methods</span></span>  
  
|<span data-ttu-id="09392-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="09392-105">Method</span></span>|<span data-ttu-id="09392-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09392-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09392-107">Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="09392-108">Konağın geçerli örnek tarafından temsil ettiği görevi `IHostTask` uyandırmasını, bu nedenle görevin iptal edileceğini ister.</span><span class="sxs-lookup"><span data-stu-id="09392-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="09392-109">GetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="09392-110">Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="09392-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="09392-111">Join Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-111">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="09392-112">Geçerli örnek tarafından temsil edilen görev `IHostTask` tamamlanana kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](ihosttask-alert-method.md) çağrıldığında çağıran görevi engeller.</span><span class="sxs-lookup"><span data-stu-id="09392-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="09392-113">SetCLRTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-113">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="09392-114">Bir [ICLRTask arabirimi](iclrtask-interface.md) örneğini geçerli `IHostTask` örnekle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="09392-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="09392-115">SetPriority Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="09392-116">Konağın, geçerli örnek tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="09392-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="09392-117">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="09392-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="09392-118">Konağın geçerli örnek tarafından temsil edilen görevi `IHostTask` askıya alınmış bir durumdan canlı duruma taşımasını ister, bu da kodun yürütülebileceğini.</span><span class="sxs-lookup"><span data-stu-id="09392-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09392-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09392-119">Remarks</span></span>  

 <span data-ttu-id="09392-120">CLR, `IHostTask` bir görevi başlatmak, iş parçacığı öncelik düzeyini ayarlamak ve daha fazlasını yapmak için tarafından tanımlanan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="09392-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09392-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09392-121">Requirements</span></span>  

 <span data-ttu-id="09392-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09392-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09392-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09392-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09392-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="09392-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09392-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09392-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09392-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09392-126">See also</span></span>

- [<span data-ttu-id="09392-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09392-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="09392-128">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09392-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="09392-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09392-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="09392-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09392-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
