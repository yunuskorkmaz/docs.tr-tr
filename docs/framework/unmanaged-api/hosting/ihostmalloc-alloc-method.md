---
title: "IHostMAlloc::Alloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Alloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9cc4447424d1594f6fa86e07be659a6ba97f0427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="aeb22-102">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeb22-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="aeb22-103">Ana bilgisayar yığınından belirli bellek miktarını tahsis istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="aeb22-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeb22-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aeb22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeb22-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="aeb22-106">[in] Geçerli bellek ayırma isteği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="aeb22-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="aeb22-107">[in] Aşağıdakilerden birini [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="aeb22-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="aeb22-108">[out] Bir işaretçi ayrılmış bellek ya da istek tamamlanamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="aeb22-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeb22-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aeb22-109">Return Value</span></span>  
  
|<span data-ttu-id="aeb22-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aeb22-110">HRESULT</span></span>|<span data-ttu-id="aeb22-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeb22-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aeb22-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="aeb22-112">S_OK</span></span>|<span data-ttu-id="aeb22-113">`Alloc`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aeb22-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="aeb22-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aeb22-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aeb22-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aeb22-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aeb22-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aeb22-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aeb22-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aeb22-117">The call timed out.</span></span>|  
|<span data-ttu-id="aeb22-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aeb22-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aeb22-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="aeb22-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aeb22-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aeb22-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aeb22-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="aeb22-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aeb22-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aeb22-122">E_FAIL</span></span>|<span data-ttu-id="aeb22-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aeb22-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aeb22-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aeb22-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aeb22-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb22-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aeb22-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aeb22-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aeb22-127">Ayırma isteği tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="aeb22-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb22-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeb22-128">Remarks</span></span>  
 <span data-ttu-id="aeb22-129">CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aeb22-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb22-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeb22-130">Requirements</span></span>  
 <span data-ttu-id="aeb22-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb22-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb22-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb22-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb22-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aeb22-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb22-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb22-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb22-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb22-135">See Also</span></span>  
 [<span data-ttu-id="aeb22-136">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb22-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="aeb22-137">Ihostmalloc arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb22-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
