---
title: "IHostMemoryManager::VirtualAlloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="43c55-102">IHostMemoryManager::VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43c55-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="43c55-103">Karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="43c55-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="43c55-104">Win32 uygulaması `VirtualAlloc` ayırır ya da bir bölge çağırma işleminin sanal adres alanındaki sayfaların kaydeder.</span><span class="sxs-lookup"><span data-stu-id="43c55-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43c55-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43c55-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43c55-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="43c55-107">[in] Başlangıç adresi ayırmak için bölge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43c55-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="43c55-108">[in] Bölgenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="43c55-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="43c55-109">[in] Bellek ayırma türü.</span><span class="sxs-lookup"><span data-stu-id="43c55-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="43c55-110">[in] Bölge için bellek koruma ayrılması sayfaların.</span><span class="sxs-lookup"><span data-stu-id="43c55-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="43c55-111">[in] Bir [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="43c55-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="43c55-112">[out] Başlangıç adresi isteği uyulmadığını yoksa null değerini veya ayrılmış bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="43c55-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43c55-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43c55-113">Return Value</span></span>  
  
|<span data-ttu-id="43c55-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43c55-114">HRESULT</span></span>|<span data-ttu-id="43c55-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43c55-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43c55-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="43c55-116">S_OK</span></span>|<span data-ttu-id="43c55-117">`VirtualAlloc`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="43c55-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="43c55-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43c55-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43c55-119">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="43c55-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43c55-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43c55-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43c55-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="43c55-121">The call timed out.</span></span>|  
|<span data-ttu-id="43c55-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43c55-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43c55-123">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="43c55-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43c55-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43c55-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43c55-125">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="43c55-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43c55-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43c55-126">E_FAIL</span></span>|<span data-ttu-id="43c55-127">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="43c55-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43c55-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43c55-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43c55-129">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="43c55-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="43c55-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="43c55-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="43c55-131">Ayırma isteği tamamlamak yeterli bellek yoktu</span><span class="sxs-lookup"><span data-stu-id="43c55-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c55-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43c55-132">Remarks</span></span>  
 <span data-ttu-id="43c55-133">Bir bölge çağırarak işleminizi adres alanı ayırmak `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="43c55-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="43c55-134">`pAddress` Parametresi istediğiniz bellek bloğu başlangıç adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="43c55-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="43c55-135">Bu parametre genellikle null.</span><span class="sxs-lookup"><span data-stu-id="43c55-135">This parameter is typically set to null.</span></span> <span data-ttu-id="43c55-136">İşletim sistemi bir kayıt işlemi için kullanılabilir boş adres aralıklarının tutar.</span><span class="sxs-lookup"><span data-stu-id="43c55-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="43c55-137">A `pAddress` null değeri görür uygun yerlerde bölge ayrılacak sistem bildirir.</span><span class="sxs-lookup"><span data-stu-id="43c55-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="43c55-138">Alternatif olarak, belirli bir başlangıç adresi için bellek bloğu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="43c55-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="43c55-139">Her iki durumda da çıkış parametresi `ppMem` işaretçi olarak ayrılan belleği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43c55-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="43c55-140">İşlevi bir HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="43c55-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="43c55-141">Win32 `VirtualAlloc` işlevi yok bir `ppMem` parametresi ve bunun yerine ayrılmış bellek işaretçisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="43c55-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="43c55-142">Daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="43c55-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43c55-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43c55-143">Requirements</span></span>  
 <span data-ttu-id="43c55-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43c55-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c55-145">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43c55-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43c55-146">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="43c55-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43c55-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c55-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c55-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43c55-148">See Also</span></span>  
 [<span data-ttu-id="43c55-149">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43c55-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
