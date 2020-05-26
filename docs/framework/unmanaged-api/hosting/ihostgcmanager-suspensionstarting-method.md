---
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
ms.openlocfilehash: f2b4028c78daf266e4ffecd86e6b0b30b9607d5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804814"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="65f64-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65f64-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="65f64-103">Bir atık toplama işlemi gerçekleştirmek için ortak dil çalışma zamanının (CLR) görevlerin yürütülmesini askıya alıp konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="65f64-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f64-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="65f64-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="65f64-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65f64-105">Return Value</span></span>  
  
|<span data-ttu-id="65f64-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65f64-106">HRESULT</span></span>|<span data-ttu-id="65f64-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65f64-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65f64-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="65f64-108">S_OK</span></span>|<span data-ttu-id="65f64-109">`SuspensionStarting`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="65f64-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="65f64-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65f64-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65f64-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="65f64-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65f64-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65f64-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65f64-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="65f64-113">The call timed out.</span></span>|  
|<span data-ttu-id="65f64-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65f64-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65f64-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="65f64-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65f64-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65f64-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65f64-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="65f64-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65f64-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65f64-118">E_FAIL</span></span>|<span data-ttu-id="65f64-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="65f64-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65f64-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="65f64-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65f64-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="65f64-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65f64-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65f64-122">Remarks</span></span>  
 <span data-ttu-id="65f64-123">CLR, `SuspensionStarting` atık toplamanın meydana geldiğini konağa bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="65f64-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65f64-124">Bu görevi yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="65f64-124">Do not reschedule this task.</span></span> <span data-ttu-id="65f64-125">[Threadisblockingforaskıya](ihostgcmanager-threadisblockingforsuspension-method.md) alma çağrıldığında konağın bir görevi yeniden zamanlamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="65f64-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f64-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65f64-126">Requirements</span></span>  
 <span data-ttu-id="65f64-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f64-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f64-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65f64-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65f64-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="65f64-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65f64-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f64-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f64-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f64-131">See also</span></span>

- [<span data-ttu-id="65f64-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f64-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="65f64-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f64-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="65f64-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f64-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="65f64-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f64-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="65f64-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65f64-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
