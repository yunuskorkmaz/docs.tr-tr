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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3e808c7ed03d7b4cc9dfe77389df6b2eff491f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937717"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="54e07-102">IHostGCManager::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54e07-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="54e07-103">Bir atık toplama işlemi gerçekleştirmek için ortak dil çalışma zamanının (CLR) görevlerin yürütülmesini askıya alıp konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="54e07-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54e07-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="54e07-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54e07-105">Return Value</span></span>  
  
|<span data-ttu-id="54e07-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54e07-106">HRESULT</span></span>|<span data-ttu-id="54e07-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e07-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54e07-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="54e07-108">S_OK</span></span>|<span data-ttu-id="54e07-109">`SuspensionStarting`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="54e07-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="54e07-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54e07-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54e07-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="54e07-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54e07-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54e07-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54e07-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="54e07-113">The call timed out.</span></span>|  
|<span data-ttu-id="54e07-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54e07-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54e07-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="54e07-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54e07-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54e07-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54e07-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="54e07-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54e07-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54e07-118">E_FAIL</span></span>|<span data-ttu-id="54e07-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="54e07-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54e07-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54e07-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54e07-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="54e07-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54e07-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54e07-122">Remarks</span></span>  
 <span data-ttu-id="54e07-123">CLR, atık `SuspensionStarting` toplamanın meydana geldiğini konağa bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="54e07-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="54e07-124">Bu görevi yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="54e07-124">Do not reschedule this task.</span></span> <span data-ttu-id="54e07-125">[Threadisblockingforaskıya](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) alma çağrıldığında konağın bir görevi yeniden zamanlamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54e07-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54e07-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54e07-126">Requirements</span></span>  
 <span data-ttu-id="54e07-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54e07-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54e07-128">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54e07-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54e07-129">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="54e07-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54e07-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54e07-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e07-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e07-131">See also</span></span>

- [<span data-ttu-id="54e07-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e07-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="54e07-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e07-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="54e07-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e07-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="54e07-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e07-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="54e07-136">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e07-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
