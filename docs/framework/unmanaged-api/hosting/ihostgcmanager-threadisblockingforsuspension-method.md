---
description: 'Şu konuda daha fazla bilgi edinin: IHostGCManager:: Threadisblockingforaskıya alma yöntemi'
title: IHostGCManager::ThreadIsBlockingForSuspension Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 9cb07b80fa9aad1ac289bc5a3abb5a4760f2bfc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708648"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="7f0bd-103">IHostGCManager::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-103">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="7f0bd-104">Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-104">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f0bd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f0bd-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7f0bd-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f0bd-106">Return Value</span></span>  
  
|<span data-ttu-id="7f0bd-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f0bd-107">HRESULT</span></span>|<span data-ttu-id="7f0bd-108">Description</span><span class="sxs-lookup"><span data-stu-id="7f0bd-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f0bd-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f0bd-109">S_OK</span></span>|<span data-ttu-id="7f0bd-110">`ThreadIsBlockingForSuspension` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-110">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="7f0bd-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f0bd-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f0bd-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f0bd-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f0bd-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f0bd-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-114">The call timed out.</span></span>|  
|<span data-ttu-id="7f0bd-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f0bd-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f0bd-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f0bd-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f0bd-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f0bd-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f0bd-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f0bd-119">E_FAIL</span></span>|<span data-ttu-id="7f0bd-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f0bd-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f0bd-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f0bd-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f0bd-123">Remarks</span></span>  

 <span data-ttu-id="7f0bd-124">CLR, `ThreadIsBlockForSuspension` ana bilgisayara yönetilmeyen görevler için iş parçacığını yeniden zamanlama fırsatı vermek üzere bir çöp toplama hazırlığı için genellikle yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-124">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f0bd-125">Konak, yalnızca öğesine yapılan çağrıdan sonra görevleri yeniden zamanlayabilir `ThreadIsBlockingForSuspension` .</span><span class="sxs-lookup"><span data-stu-id="7f0bd-125">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="7f0bd-126">Çalışma zamanı [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md)öğesini çağırdıktan sonra konağın bir görevi yeniden zamanlamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-126">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f0bd-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f0bd-127">Requirements</span></span>  

 <span data-ttu-id="7f0bd-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f0bd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f0bd-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f0bd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f0bd-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f0bd-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f0bd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f0bd-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0bd-132">See also</span></span>

- [<span data-ttu-id="7f0bd-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7f0bd-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7f0bd-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7f0bd-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7f0bd-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f0bd-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
