---
description: ': IHostMemoryManager:: VirtualAlloc yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 28682aea5e6e7951b3b8f0a9af946a3f3828601b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707858"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="5d0fa-103">IHostMemoryManager::VirtualAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d0fa-103">IHostMemoryManager::VirtualAlloc Method</span></span>

<span data-ttu-id="5d0fa-104">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="5d0fa-105">Win32 uygulamasının, `VirtualAlloc` çağıran işlemin sanal adres alanındaki bir sayfa bölgesini ayırır veya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-105">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0fa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d0fa-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5d0fa-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d0fa-107">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="5d0fa-108">'ndaki Ayrılacak bölgenin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-108">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="5d0fa-109">'ndaki Bölgenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-109">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="5d0fa-110">'ndaki Bellek ayırma türü.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-110">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="5d0fa-111">'ndaki Ayrılacak sayfa bölgesi için bellek koruması.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-111">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5d0fa-112">'ndaki Bir ayırma hatasının etkisini gösteren bir [Ememorycriticalhandle düzeyi](ememorycriticallevel-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-112">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5d0fa-113">dışı Ayrılan belleğin başlangıç adresine yönelik işaretçi veya istek karşılanmıyorsa null.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-113">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d0fa-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d0fa-114">Return Value</span></span>  
  
|<span data-ttu-id="5d0fa-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d0fa-115">HRESULT</span></span>|<span data-ttu-id="5d0fa-116">Description</span><span class="sxs-lookup"><span data-stu-id="5d0fa-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d0fa-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d0fa-117">S_OK</span></span>|<span data-ttu-id="5d0fa-118">`VirtualAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-118">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="5d0fa-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d0fa-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d0fa-120">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d0fa-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d0fa-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d0fa-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-122">The call timed out.</span></span>|  
|<span data-ttu-id="5d0fa-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d0fa-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d0fa-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d0fa-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d0fa-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d0fa-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d0fa-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d0fa-127">E_FAIL</span></span>|<span data-ttu-id="5d0fa-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d0fa-129">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d0fa-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5d0fa-131">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5d0fa-131">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5d0fa-132">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu</span><span class="sxs-lookup"><span data-stu-id="5d0fa-132">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d0fa-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d0fa-133">Remarks</span></span>  

 <span data-ttu-id="5d0fa-134">' İ çağırarak, işleminizin adres alanında bir bölgeyi ayırabilirsiniz `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="5d0fa-134">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="5d0fa-135">Parametresi, istediğiniz `pAddress` bellek bloğunun başlangıç adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-135">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="5d0fa-136">Bu parametre genellikle null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-136">This parameter is typically set to null.</span></span> <span data-ttu-id="5d0fa-137">İşletim sistemi, işlem için kullanılabilen boş adres aralıklarının bir kaydını tutar.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-137">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="5d0fa-138">`pAddress`Null değeri, sisteme uygun olduğu yerde bölge ayırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-138">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="5d0fa-139">Alternatif olarak, bellek bloğu için belirli bir başlangıç adresi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-139">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="5d0fa-140">Her iki durumda da, çıkış parametresi `ppMem` ayrılan belleğe bir işaretçi olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-140">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="5d0fa-141">İşlevin kendisi bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-141">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="5d0fa-142">Win32 `VirtualAlloc` işlevinin bir `ppMem` parametresi yoktur ve bunun yerine, ayrılan belleğe işaretçiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-142">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="5d0fa-143">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-143">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d0fa-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d0fa-144">Requirements</span></span>  

 <span data-ttu-id="5d0fa-145">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d0fa-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d0fa-146">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d0fa-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d0fa-147">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5d0fa-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d0fa-148">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d0fa-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0fa-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d0fa-149">See also</span></span>

- [<span data-ttu-id="5d0fa-150">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d0fa-150">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
