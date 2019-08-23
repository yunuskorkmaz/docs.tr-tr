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
ms.openlocfilehash: 29311f00f5ac4b61380b57cdd9fda07ec7de1b23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966200"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="08d2a-102">ICLRGCManager::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d2a-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="08d2a-103">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08d2a-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08d2a-104">4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu [ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük `DWORD` değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08d2a-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08d2a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08d2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08d2a-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="08d2a-107">'ndaki Bir çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="08d2a-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="08d2a-108">En küçük kesim boyutu 4 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="08d2a-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="08d2a-109">Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="08d2a-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="08d2a-110">'ndaki Oluşturma 0 için belirtilen en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="08d2a-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="08d2a-111">Minimum nesil 0 boyutu 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="08d2a-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08d2a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08d2a-112">Return Value</span></span>  
  
|<span data-ttu-id="08d2a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08d2a-113">HRESULT</span></span>|<span data-ttu-id="08d2a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d2a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08d2a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="08d2a-115">S_OK</span></span>|<span data-ttu-id="08d2a-116">`SetGCStartupLimits`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="08d2a-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="08d2a-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08d2a-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08d2a-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="08d2a-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08d2a-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08d2a-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08d2a-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="08d2a-120">The call timed out.</span></span>|  
|<span data-ttu-id="08d2a-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08d2a-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08d2a-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="08d2a-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08d2a-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08d2a-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08d2a-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="08d2a-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08d2a-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08d2a-125">E_FAIL</span></span>|<span data-ttu-id="08d2a-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="08d2a-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08d2a-127">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="08d2a-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08d2a-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="08d2a-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d2a-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08d2a-129">Remarks</span></span>  
 <span data-ttu-id="08d2a-130">`SetGCStartupLimits` Ayarlayan değerler yalnızca bir kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="08d2a-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="08d2a-131">Daha sonraki çağrıları `SetGCStartupLimits` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="08d2a-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d2a-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08d2a-132">Requirements</span></span>  
 <span data-ttu-id="08d2a-133">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d2a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d2a-134">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08d2a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08d2a-135">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="08d2a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08d2a-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d2a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d2a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08d2a-137">See also</span></span>

- [<span data-ttu-id="08d2a-138">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="08d2a-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="08d2a-139">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="08d2a-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="08d2a-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08d2a-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="08d2a-141">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08d2a-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
