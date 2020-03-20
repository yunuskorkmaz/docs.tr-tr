---
title: IHostMAlloc::Alloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176311"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="66795-102">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66795-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="66795-103">Ana bilgisayar, yığından belirtilen bellek miktarını ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="66795-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66795-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66795-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66795-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66795-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="66795-106">[içinde] Geçerli bellek ayırma isteğinin baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="66795-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="66795-107">[içinde] Bir ayırma hatasının etkisini gösteren [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="66795-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="66795-108">[çıkış] Ayrılan belleğe işaretçi veya istek tamamlanamadıysa null.</span><span class="sxs-lookup"><span data-stu-id="66795-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66795-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66795-109">Return Value</span></span>  
  
|<span data-ttu-id="66795-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66795-110">HRESULT</span></span>|<span data-ttu-id="66795-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66795-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66795-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="66795-112">S_OK</span></span>|<span data-ttu-id="66795-113">`Alloc`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66795-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="66795-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66795-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66795-115">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="66795-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66795-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66795-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66795-117">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="66795-117">The call timed out.</span></span>|  
|<span data-ttu-id="66795-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66795-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66795-119">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="66795-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66795-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66795-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66795-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="66795-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66795-122">E_faıl</span><span class="sxs-lookup"><span data-stu-id="66795-122">E_FAIL</span></span>|<span data-ttu-id="66795-123">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="66795-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66795-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66795-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66795-125">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="66795-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="66795-126">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="66795-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="66795-127">Ayırma isteğini tamamlamak için yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="66795-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66795-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66795-128">Remarks</span></span>  
 <span data-ttu-id="66795-129">CLR IHostMemoryManager arayarak bir örnek için bir `IHostMalloc` arayüz işaretçisi [alır::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66795-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66795-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66795-130">Requirements</span></span>  
 <span data-ttu-id="66795-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66795-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66795-132">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66795-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66795-133">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="66795-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66795-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66795-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66795-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66795-135">See also</span></span>

- [<span data-ttu-id="66795-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66795-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="66795-137">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66795-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
