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
ms.openlocfilehash: a2a752f23ed64795f9208b9101c21bc585d5f431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136809"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="b94e7-102">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b94e7-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="b94e7-103">Konağın yığından belirtilen miktarda bellek ayırmasını ve ayrıca belleğin nerede ayrıldığını izlemelerini ister.</span><span class="sxs-lookup"><span data-stu-id="b94e7-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b94e7-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b94e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b94e7-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="b94e7-106">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b94e7-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="b94e7-107">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="b94e7-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="b94e7-108">'ndaki Hata ayıklanan yürütülebilir dosyanın kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="b94e7-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="b94e7-109">'ndaki Ayırmasının istendiği `pszFileName` satır numarası.</span><span class="sxs-lookup"><span data-stu-id="b94e7-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="b94e7-110">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="b94e7-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b94e7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b94e7-111">Return Value</span></span>  
  
|<span data-ttu-id="b94e7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b94e7-112">HRESULT</span></span>|<span data-ttu-id="b94e7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b94e7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b94e7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b94e7-114">S_OK</span></span>|<span data-ttu-id="b94e7-115">`DebugAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b94e7-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="b94e7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b94e7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b94e7-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b94e7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b94e7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b94e7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b94e7-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b94e7-119">The call timed out.</span></span>|  
|<span data-ttu-id="b94e7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b94e7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b94e7-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b94e7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b94e7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b94e7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b94e7-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b94e7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b94e7-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="b94e7-124">E_FAIL</span></span>|<span data-ttu-id="b94e7-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b94e7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b94e7-126">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b94e7-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b94e7-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b94e7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b94e7-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b94e7-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b94e7-129">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="b94e7-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b94e7-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b94e7-130">Remarks</span></span>  
 <span data-ttu-id="b94e7-131">CLR [IHostMemoryManager:: Createmayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b94e7-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="b94e7-132">`DebugAlloc`, çalışma zamanının hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b94e7-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b94e7-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b94e7-133">Requirements</span></span>  
 <span data-ttu-id="b94e7-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b94e7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b94e7-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b94e7-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b94e7-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b94e7-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b94e7-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b94e7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94e7-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b94e7-138">See also</span></span>

- [<span data-ttu-id="b94e7-139">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b94e7-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b94e7-140">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b94e7-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
