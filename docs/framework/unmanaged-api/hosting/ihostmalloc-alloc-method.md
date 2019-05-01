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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32499e74e8af9a865347bd800d3db4c303a7344c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796740"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="b83d0-102">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b83d0-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="b83d0-103">İstekleri konak yığından bellek belirtilen miktarı ayırın.</span><span class="sxs-lookup"><span data-stu-id="b83d0-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b83d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b83d0-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b83d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b83d0-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="b83d0-106">[in] Bayt cinsinden geçerli bellek ayırma isteği boyutu.</span><span class="sxs-lookup"><span data-stu-id="b83d0-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="b83d0-107">[in] Aşağıdakilerden birini [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="b83d0-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="b83d0-108">[out] Ayrılan bellek ya da istek tamamlanamadı, null bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b83d0-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b83d0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b83d0-109">Return Value</span></span>  
  
|<span data-ttu-id="b83d0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b83d0-110">HRESULT</span></span>|<span data-ttu-id="b83d0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b83d0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b83d0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b83d0-112">S_OK</span></span>|<span data-ttu-id="b83d0-113">`Alloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b83d0-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="b83d0-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b83d0-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b83d0-115">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="b83d0-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b83d0-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b83d0-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b83d0-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b83d0-117">The call timed out.</span></span>|  
|<span data-ttu-id="b83d0-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b83d0-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b83d0-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b83d0-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b83d0-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b83d0-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b83d0-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b83d0-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b83d0-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b83d0-122">E_FAIL</span></span>|<span data-ttu-id="b83d0-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b83d0-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b83d0-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b83d0-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b83d0-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b83d0-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b83d0-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b83d0-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b83d0-127">Ayırma isteğinin tamamlanması yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="b83d0-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b83d0-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b83d0-128">Remarks</span></span>  
 <span data-ttu-id="b83d0-129">CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b83d0-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b83d0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b83d0-130">Requirements</span></span>  
 <span data-ttu-id="b83d0-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b83d0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b83d0-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b83d0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b83d0-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b83d0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b83d0-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b83d0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83d0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b83d0-135">See also</span></span>

- [<span data-ttu-id="b83d0-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b83d0-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b83d0-137">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b83d0-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
