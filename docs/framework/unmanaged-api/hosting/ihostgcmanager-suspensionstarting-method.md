---
description: 'Daha fazla bilgi edinin: IHostGCManager:: SuspensionStarting yöntemi'
title: IHostGCManager::SuspensionStarting Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
ms.openlocfilehash: 3a57d47fea735ab004fd0db293bed1ba4d3314e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708651"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="6411c-103">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6411c-103">IHostGCManager::SuspensionStarting Method</span></span>

<span data-ttu-id="6411c-104">Bir atık toplama işlemi gerçekleştirmek için ortak dil çalışma zamanının (CLR) görevlerin yürütülmesini askıya alıp konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="6411c-104">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6411c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6411c-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6411c-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6411c-106">Return Value</span></span>  
  
|<span data-ttu-id="6411c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6411c-107">HRESULT</span></span>|<span data-ttu-id="6411c-108">Description</span><span class="sxs-lookup"><span data-stu-id="6411c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6411c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6411c-109">S_OK</span></span>|<span data-ttu-id="6411c-110">`SuspensionStarting` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6411c-110">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="6411c-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6411c-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6411c-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6411c-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6411c-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6411c-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6411c-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6411c-114">The call timed out.</span></span>|  
|<span data-ttu-id="6411c-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6411c-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6411c-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6411c-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6411c-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6411c-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6411c-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6411c-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6411c-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6411c-119">E_FAIL</span></span>|<span data-ttu-id="6411c-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6411c-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6411c-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6411c-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6411c-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6411c-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6411c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6411c-123">Remarks</span></span>  

 <span data-ttu-id="6411c-124">CLR, `SuspensionStarting` atık toplamanın meydana geldiğini konağa bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="6411c-124">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6411c-125">Bu görevi yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="6411c-125">Do not reschedule this task.</span></span> <span data-ttu-id="6411c-126">[Threadisblockingforaskıya](ihostgcmanager-threadisblockingforsuspension-method.md) alma çağrıldığında konağın bir görevi yeniden zamanlamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6411c-126">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6411c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6411c-127">Requirements</span></span>  

 <span data-ttu-id="6411c-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6411c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6411c-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6411c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6411c-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6411c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6411c-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6411c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6411c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6411c-132">See also</span></span>

- [<span data-ttu-id="6411c-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6411c-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6411c-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6411c-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6411c-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6411c-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6411c-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6411c-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="6411c-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6411c-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
