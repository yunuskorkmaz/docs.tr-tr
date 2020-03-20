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
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178031"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="314b6-102">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="314b6-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="314b6-103">Ana bilgisayar, yığından belirtilen bellek miktarını ayırmasını ve ayrıca belleğin nereye tahsis edildiğini izlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="314b6-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="314b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="314b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="314b6-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="314b6-106">[içinde] Geçerli bellek ayırma isteğinin baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="314b6-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="314b6-107">[içinde] Bir ayırma hatasının etkisini gösteren [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="314b6-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="314b6-108">[içinde] Yürütülebilir kod dosyası debugged ediliyor.</span><span class="sxs-lookup"><span data-stu-id="314b6-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="314b6-109">[içinde] Ayırmanın istendiği `pszFileName` satır numarası.</span><span class="sxs-lookup"><span data-stu-id="314b6-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="314b6-110">[çıkış] Ayrılan belleğe işaretçi veya istek tamamlanamadıysa null.</span><span class="sxs-lookup"><span data-stu-id="314b6-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="314b6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="314b6-111">Return Value</span></span>  
  
|<span data-ttu-id="314b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="314b6-112">HRESULT</span></span>|<span data-ttu-id="314b6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="314b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="314b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="314b6-114">S_OK</span></span>|<span data-ttu-id="314b6-115">`DebugAlloc`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="314b6-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="314b6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="314b6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="314b6-117">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="314b6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="314b6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="314b6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="314b6-119">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="314b6-119">The call timed out.</span></span>|  
|<span data-ttu-id="314b6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="314b6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="314b6-121">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="314b6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="314b6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="314b6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="314b6-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="314b6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="314b6-124">E_faıl</span><span class="sxs-lookup"><span data-stu-id="314b6-124">E_FAIL</span></span>|<span data-ttu-id="314b6-125">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="314b6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="314b6-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="314b6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="314b6-127">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="314b6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="314b6-128">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="314b6-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="314b6-129">Ayırma isteğini tamamlamak için yeterli bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="314b6-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="314b6-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="314b6-130">Remarks</span></span>  
 <span data-ttu-id="314b6-131">CLR IHostMemoryManager arayarak bir [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) örnek için bir arayüz işaretçisi [alır::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="314b6-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="314b6-132">`DebugAlloc`hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almak için çalışma süresi sağlar.</span><span class="sxs-lookup"><span data-stu-id="314b6-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="314b6-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="314b6-133">Requirements</span></span>  
 <span data-ttu-id="314b6-134">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314b6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314b6-135">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="314b6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="314b6-136">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="314b6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="314b6-137">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314b6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314b6-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314b6-138">See also</span></span>

- [<span data-ttu-id="314b6-139">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314b6-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="314b6-140">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="314b6-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
