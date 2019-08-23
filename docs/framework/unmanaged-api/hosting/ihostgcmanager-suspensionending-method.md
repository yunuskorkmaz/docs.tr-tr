---
title: IHostGCManager::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f65f924b872195000f73bf29b267d1fc30b74f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937724"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="ad7d6-102">IHostGCManager::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="ad7d6-103">Ana bilgisayara ortak dil çalışma zamanının (CLR) bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin devam ettirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad7d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad7d6-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="ad7d6-106">'ndaki İş parçacığının devam etmesinden önce son kullanılan çöp toplama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad7d6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad7d6-107">Return Value</span></span>  
  
|<span data-ttu-id="ad7d6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad7d6-108">HRESULT</span></span>|<span data-ttu-id="ad7d6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad7d6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad7d6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad7d6-110">S_OK</span></span>|<span data-ttu-id="ad7d6-111">`SuspensionEnding`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="ad7d6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad7d6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad7d6-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad7d6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad7d6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad7d6-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-115">The call timed out.</span></span>|  
|<span data-ttu-id="ad7d6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad7d6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad7d6-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad7d6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad7d6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad7d6-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad7d6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad7d6-120">E_FAIL</span></span>|<span data-ttu-id="ad7d6-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad7d6-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad7d6-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad7d6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad7d6-124">Remarks</span></span>  
 <span data-ttu-id="ad7d6-125">CLR, bir `SuspensionEnding` atık toplama gerçekleştirdikten sonra, Konağı iş parçacığının yürütmeyi sürdürmesini bildirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad7d6-126">Yöntem çağrısının yapıldığı iş parçacığını yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad7d6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad7d6-127">Requirements</span></span>  
 <span data-ttu-id="ad7d6-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad7d6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7d6-129">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad7d6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad7d6-130">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ad7d6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad7d6-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7d6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7d6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad7d6-132">See also</span></span>

- [<span data-ttu-id="ad7d6-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ad7d6-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ad7d6-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ad7d6-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="ad7d6-137">IHostGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad7d6-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
