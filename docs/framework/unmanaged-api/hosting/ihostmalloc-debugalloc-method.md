---
title: "IHostMAlloc::DebugAlloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.DebugAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18759aa319bf39c49418e3b9388d96829ed52f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="b04b0-102">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b04b0-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="b04b0-103">Ana bilgisayar belirli bellek miktarını yığınından ayırın ve ayrıca burada belleği ayrıldı izlemek ister.</span><span class="sxs-lookup"><span data-stu-id="b04b0-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b04b0-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b04b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b04b0-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="b04b0-106">[in] Geçerli bellek ayırma isteği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b04b0-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="b04b0-107">[in] Aşağıdakilerden birini [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="b04b0-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="b04b0-108">[in] Ayıklanacak yürütülebilir kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="b04b0-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="b04b0-109">[in] Satır numarasında `pszFileName` burada ayırma işlemi istendi.</span><span class="sxs-lookup"><span data-stu-id="b04b0-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="b04b0-110">[out] Bir işaretçi ayrılmış bellek ya da istek tamamlanamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="b04b0-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b04b0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b04b0-111">Return Value</span></span>  
  
|<span data-ttu-id="b04b0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b04b0-112">HRESULT</span></span>|<span data-ttu-id="b04b0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b04b0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b04b0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b04b0-114">S_OK</span></span>|<span data-ttu-id="b04b0-115">`DebugAlloc`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b04b0-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="b04b0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b04b0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b04b0-117">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b04b0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b04b0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b04b0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b04b0-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b04b0-119">The call timed out.</span></span>|  
|<span data-ttu-id="b04b0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b04b0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b04b0-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b04b0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b04b0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b04b0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b04b0-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b04b0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b04b0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b04b0-124">E_FAIL</span></span>|<span data-ttu-id="b04b0-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b04b0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b04b0-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b04b0-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b04b0-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b04b0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b04b0-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b04b0-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b04b0-129">Ayırma isteği tamamlamak yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="b04b0-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b04b0-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b04b0-130">Remarks</span></span>  
 <span data-ttu-id="b04b0-131">CLR bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04b0-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="b04b0-132">`DebugAlloc`hata ayıklama sırasında kullanmak için kodu dosya bilgileri almak çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b04b0-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04b0-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b04b0-133">Requirements</span></span>  
 <span data-ttu-id="b04b0-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b04b0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04b0-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b04b0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b04b0-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b04b0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b04b0-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04b0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04b0-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b04b0-138">See Also</span></span>  
 [<span data-ttu-id="b04b0-139">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="b04b0-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="b04b0-140">Ihostmalloc arabirimi</span><span class="sxs-lookup"><span data-stu-id="b04b0-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
