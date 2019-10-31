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
ms.openlocfilehash: dd588fa85ff8aaa396a8d0e52a738ada46c2a9b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128610"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="15b92-102">IHostMemoryManager::VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15b92-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="15b92-103">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="15b92-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="15b92-104">`VirtualAlloc` Win32 uygulamasının, çağıran işlemin sanal adres alanındaki bir sayfa bölgesini ayırır veya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="15b92-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15b92-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15b92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15b92-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="15b92-107">'ndaki Ayrılacak bölgenin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15b92-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="15b92-108">'ndaki Bölgenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="15b92-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="15b92-109">'ndaki Bellek ayırma türü.</span><span class="sxs-lookup"><span data-stu-id="15b92-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="15b92-110">'ndaki Ayrılacak sayfa bölgesi için bellek koruması.</span><span class="sxs-lookup"><span data-stu-id="15b92-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="15b92-111">'ndaki Bir ayırma hatasının etkisini gösteren bir [Ememorycriticalhandle düzeyi](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="15b92-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="15b92-112">dışı Ayrılan belleğin başlangıç adresine yönelik işaretçi veya istek karşılanmıyorsa null.</span><span class="sxs-lookup"><span data-stu-id="15b92-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15b92-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15b92-113">Return Value</span></span>  
  
|<span data-ttu-id="15b92-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15b92-114">HRESULT</span></span>|<span data-ttu-id="15b92-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15b92-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15b92-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="15b92-116">S_OK</span></span>|<span data-ttu-id="15b92-117">`VirtualAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="15b92-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="15b92-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15b92-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15b92-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="15b92-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15b92-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15b92-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15b92-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="15b92-121">The call timed out.</span></span>|  
|<span data-ttu-id="15b92-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15b92-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15b92-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="15b92-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15b92-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15b92-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15b92-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="15b92-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15b92-126">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="15b92-126">E_FAIL</span></span>|<span data-ttu-id="15b92-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="15b92-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15b92-128">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="15b92-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15b92-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="15b92-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="15b92-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="15b92-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="15b92-131">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu</span><span class="sxs-lookup"><span data-stu-id="15b92-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15b92-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15b92-132">Remarks</span></span>  
 <span data-ttu-id="15b92-133">`VirtualAlloc`çağırarak, işleminizin adres alanında bir bölgeyi ayırtın.</span><span class="sxs-lookup"><span data-stu-id="15b92-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="15b92-134">`pAddress` parametresi, istediğiniz bellek bloğunun başlangıç adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="15b92-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="15b92-135">Bu parametre genellikle null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="15b92-135">This parameter is typically set to null.</span></span> <span data-ttu-id="15b92-136">İşletim sistemi, işlem için kullanılabilen boş adres aralıklarının bir kaydını tutar.</span><span class="sxs-lookup"><span data-stu-id="15b92-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="15b92-137">Null `pAddress` değeri, sistemi, bölgenin uygun olduğu her yerde ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="15b92-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="15b92-138">Alternatif olarak, bellek bloğu için belirli bir başlangıç adresi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b92-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="15b92-139">Her iki durumda da, çıkış parametresi `ppMem` ayrılan belleğe bir işaretçi olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="15b92-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="15b92-140">İşlevin kendisi bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="15b92-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="15b92-141">Win32 `VirtualAlloc` işlevi bir `ppMem` parametresine sahip değildir ve onun yerine ayrılmış belleğe işaretçiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="15b92-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="15b92-142">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="15b92-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15b92-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15b92-143">Requirements</span></span>  
 <span data-ttu-id="15b92-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b92-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b92-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15b92-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15b92-146">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="15b92-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15b92-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15b92-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b92-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15b92-148">See also</span></span>

- [<span data-ttu-id="15b92-149">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15b92-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
