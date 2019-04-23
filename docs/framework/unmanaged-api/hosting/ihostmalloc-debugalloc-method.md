---
title: IHostMAlloc::DebugAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e089d133374f112dea13e91f9bd571bd2b5af07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132931"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="3610a-102">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3610a-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="3610a-103">Konak yığından bellek belirtilen miktarı ayırın ve ayrıca bellek ayrıldığı izlemek ister.</span><span class="sxs-lookup"><span data-stu-id="3610a-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3610a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3610a-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3610a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3610a-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="3610a-106">[in] Bayt cinsinden geçerli bellek ayırma isteği boyutu.</span><span class="sxs-lookup"><span data-stu-id="3610a-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="3610a-107">[in] Aşağıdakilerden birini [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="3610a-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="3610a-108">[in] Kod dosyası hata ayıklaması yapılan yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="3610a-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="3610a-109">[in] Satır numarasını `pszFileName` burada ayırma işlemi istendi.</span><span class="sxs-lookup"><span data-stu-id="3610a-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="3610a-110">[out] Ayrılan bellek ya da istek tamamlanamadı, null bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3610a-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3610a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3610a-111">Return Value</span></span>  
  
|<span data-ttu-id="3610a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3610a-112">HRESULT</span></span>|<span data-ttu-id="3610a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3610a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3610a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3610a-114">S_OK</span></span>|<span data-ttu-id="3610a-115">`DebugAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3610a-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="3610a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3610a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3610a-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3610a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3610a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3610a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3610a-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3610a-119">The call timed out.</span></span>|  
|<span data-ttu-id="3610a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3610a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3610a-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3610a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3610a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3610a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3610a-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3610a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3610a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3610a-124">E_FAIL</span></span>|<span data-ttu-id="3610a-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3610a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3610a-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3610a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3610a-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3610a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3610a-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3610a-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3610a-129">Ayırma isteğinin tamamlanması yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="3610a-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3610a-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3610a-130">Remarks</span></span>  
 <span data-ttu-id="3610a-131">CLR bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3610a-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="3610a-132">`DebugAlloc` hata ayıklama sırasında kullanım için kod dosyası bilgileri almak çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3610a-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3610a-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3610a-133">Requirements</span></span>  
 <span data-ttu-id="3610a-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3610a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3610a-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3610a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3610a-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3610a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3610a-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3610a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3610a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3610a-138">See also</span></span>

- [<span data-ttu-id="3610a-139">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3610a-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="3610a-140">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3610a-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
