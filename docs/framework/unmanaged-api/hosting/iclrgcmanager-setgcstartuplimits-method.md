---
title: ICLRGCManager::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3292fae0ca78615faee4cb5208aa711fea9a0a24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490014"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="7d355-102">ICLRGCManager::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d355-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="7d355-103">Bir çöp toplama kesim boyutunu ve çöp toplama sistemin nesil 0 en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d355-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d355-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kesim boyutu ayarlayabileceğiniz ve en fazla nesil 0 boyutu daha büyük değerler `DWORD` kullanarak [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d355-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d355-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d355-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d355-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d355-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="7d355-107">[in] Bir çöp toplama kesim belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="7d355-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="7d355-108">En düşük kesim boyutu 4 MB'dir.</span><span class="sxs-lookup"><span data-stu-id="7d355-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="7d355-109">Parçaları, 1 MB'lık artışlarla daha yüksek veya daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d355-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="7d355-110">[in] Nesil 0 için belirtilen en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="7d355-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="7d355-111">En düşük nesil 0, 64 KB büyüklüğünde.</span><span class="sxs-lookup"><span data-stu-id="7d355-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d355-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d355-112">Return Value</span></span>  
  
|<span data-ttu-id="7d355-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d355-113">HRESULT</span></span>|<span data-ttu-id="7d355-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d355-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d355-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d355-115">S_OK</span></span>|<span data-ttu-id="7d355-116">`SetGCStartupLimits` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7d355-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="7d355-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d355-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d355-118">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="7d355-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d355-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d355-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d355-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7d355-120">The call timed out.</span></span>|  
|<span data-ttu-id="7d355-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d355-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d355-122">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7d355-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d355-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d355-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d355-124">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="7d355-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d355-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d355-125">E_FAIL</span></span>|<span data-ttu-id="7d355-126">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7d355-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d355-127">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d355-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d355-128">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d355-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d355-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d355-129">Remarks</span></span>  
 <span data-ttu-id="7d355-130">Değerleri, `SetGCStartupLimits` kümeleri yalnızca bir kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7d355-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="7d355-131">Sonraki çağrılar `SetGCStartupLimits` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="7d355-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d355-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d355-132">Requirements</span></span>  
 <span data-ttu-id="7d355-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d355-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d355-134">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d355-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d355-135">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d355-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d355-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d355-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d355-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d355-137">See also</span></span>
- [<span data-ttu-id="7d355-138">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="7d355-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="7d355-139">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="7d355-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="7d355-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d355-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7d355-141">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d355-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
