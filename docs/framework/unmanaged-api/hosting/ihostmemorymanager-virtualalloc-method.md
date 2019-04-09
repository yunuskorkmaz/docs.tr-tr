---
title: IHostMemoryManager::VirtualAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5407a9d23833d73b2d6ef0038454f56f01d56867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087657"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="5cff1-102">IHostMemoryManager::VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cff1-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="5cff1-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="5cff1-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="5cff1-104">Win32 uygulaması `VirtualAlloc` ayırır veya çağırma işleminin sanal adres alanı sayfalarında bölgesi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5cff1-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cff1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cff1-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5cff1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cff1-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="5cff1-107">[in] Başlangıç adresi ayırmak için bölge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cff1-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="5cff1-108">[in] Alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5cff1-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="5cff1-109">[in] Bellek ayırma türü.</span><span class="sxs-lookup"><span data-stu-id="5cff1-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="5cff1-110">[in] Sayfaların ayrılacak bellek koruması bölge için.</span><span class="sxs-lookup"><span data-stu-id="5cff1-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5cff1-111">[in] Bir [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="5cff1-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5cff1-112">[out] Başlangıç adresi ayrılmış bellek ya da istek karşılanmadı, null işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cff1-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cff1-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5cff1-113">Return Value</span></span>  
  
|<span data-ttu-id="5cff1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cff1-114">HRESULT</span></span>|<span data-ttu-id="5cff1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cff1-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cff1-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cff1-116">S_OK</span></span>|`VirtualAlloc` <span data-ttu-id="5cff1-117">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5cff1-117">returned successfully.</span></span>|  
|<span data-ttu-id="5cff1-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5cff1-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5cff1-119">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="5cff1-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5cff1-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5cff1-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5cff1-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5cff1-121">The call timed out.</span></span>|  
|<span data-ttu-id="5cff1-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5cff1-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5cff1-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5cff1-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5cff1-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5cff1-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5cff1-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="5cff1-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5cff1-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5cff1-126">E_FAIL</span></span>|<span data-ttu-id="5cff1-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5cff1-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5cff1-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cff1-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5cff1-129">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cff1-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5cff1-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5cff1-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5cff1-131">Ayırma isteğinin tamamlanması yeterli bellek yoktu</span><span class="sxs-lookup"><span data-stu-id="5cff1-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cff1-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cff1-132">Remarks</span></span>  
 <span data-ttu-id="5cff1-133">Bir bölge çağırarak işleminizi adres alanında ayırmak `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="5cff1-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="5cff1-134">`pAddress` Parametresi istediğiniz bellek bloğu başlangıç adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="5cff1-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="5cff1-135">Bu parametre genellikle null.</span><span class="sxs-lookup"><span data-stu-id="5cff1-135">This parameter is typically set to null.</span></span> <span data-ttu-id="5cff1-136">İşletim sistemi süreciniz için kullanılabilir boş adres aralıkları kaydını tutar.</span><span class="sxs-lookup"><span data-stu-id="5cff1-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="5cff1-137">A `pAddress` null değerini uygun gördüğü her yerde bölge ayırmak için sistemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="5cff1-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="5cff1-138">Alternatif olarak, belirli bir başlangıç adresi için bellek bloğu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5cff1-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="5cff1-139">Her iki durumda da çıkış parametresi `ppMem` bir işaretçi olarak ayrılmış belleği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5cff1-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="5cff1-140">İşlevi, bir HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cff1-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="5cff1-141">Win32 `VirtualAlloc` işlevi yok bir `ppMem` parametresi ve ayrılan bellek için bunun yerine bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cff1-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="5cff1-142">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5cff1-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cff1-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cff1-143">Requirements</span></span>  
 <span data-ttu-id="5cff1-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cff1-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cff1-145">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5cff1-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5cff1-146">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5cff1-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5cff1-147">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5cff1-147">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5cff1-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cff1-148">See also</span></span>

- [<span data-ttu-id="5cff1-149">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cff1-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
