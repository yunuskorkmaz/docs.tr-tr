---
description: ': ICLRGCManager:: SetGCStartupLimits yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5614b41cfd7a7938cdb653d879119ddbd9560b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789989"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="072c4-103">ICLRGCManager::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="072c4-103">ICLRGCManager::SetGCStartupLimits Method</span></span>

<span data-ttu-id="072c4-104">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="072c4-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="072c4-105">4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="072c4-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="072c4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="072c4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="072c4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="072c4-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="072c4-108">'ndaki Bir çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="072c4-108">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="072c4-109">En küçük kesim boyutu 4 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="072c4-109">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="072c4-110">Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="072c4-110">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="072c4-111">'ndaki Oluşturma 0 için belirtilen en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="072c4-111">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="072c4-112">Minimum nesil 0 boyutu 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="072c4-112">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="072c4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="072c4-113">Return Value</span></span>  
  
|<span data-ttu-id="072c4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="072c4-114">HRESULT</span></span>|<span data-ttu-id="072c4-115">Description</span><span class="sxs-lookup"><span data-stu-id="072c4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="072c4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="072c4-116">S_OK</span></span>|<span data-ttu-id="072c4-117">`SetGCStartupLimits` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="072c4-117">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="072c4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="072c4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="072c4-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="072c4-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="072c4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="072c4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="072c4-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="072c4-121">The call timed out.</span></span>|  
|<span data-ttu-id="072c4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="072c4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="072c4-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="072c4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="072c4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="072c4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="072c4-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="072c4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="072c4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="072c4-126">E_FAIL</span></span>|<span data-ttu-id="072c4-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="072c4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="072c4-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="072c4-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="072c4-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="072c4-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="072c4-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="072c4-130">Remarks</span></span>  

 <span data-ttu-id="072c4-131">`SetGCStartupLimits`Ayarlayan değerler yalnızca bir kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="072c4-131">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="072c4-132">Daha sonraki çağrıları `SetGCStartupLimits` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="072c4-132">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="072c4-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="072c4-133">Requirements</span></span>  

 <span data-ttu-id="072c4-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="072c4-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="072c4-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="072c4-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="072c4-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="072c4-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="072c4-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="072c4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072c4-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="072c4-138">See also</span></span>

- [<span data-ttu-id="072c4-139">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="072c4-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="072c4-140">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="072c4-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="072c4-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="072c4-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="072c4-142">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="072c4-142">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
