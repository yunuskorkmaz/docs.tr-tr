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
ms.openlocfilehash: 3f85e7c7fd54079ddce37f739a3a7bc0fa830d31
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493298"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="949df-102">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="949df-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="949df-103">Konağın yığından belirtilen miktarda bellek ayırmasını ve ayrıca belleğin nerede ayrıldığını izlemelerini ister.</span><span class="sxs-lookup"><span data-stu-id="949df-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949df-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="949df-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="949df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="949df-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="949df-106">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="949df-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="949df-107">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="949df-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="949df-108">'ndaki Hata ayıklanan yürütülebilir dosyanın kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="949df-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="949df-109">'ndaki Ayırmanın istendiği satır numarası `pszFileName` .</span><span class="sxs-lookup"><span data-stu-id="949df-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="949df-110">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="949df-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="949df-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="949df-111">Return Value</span></span>  
  
|<span data-ttu-id="949df-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="949df-112">HRESULT</span></span>|<span data-ttu-id="949df-113">Description</span><span class="sxs-lookup"><span data-stu-id="949df-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="949df-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="949df-114">S_OK</span></span>|<span data-ttu-id="949df-115">`DebugAlloc`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="949df-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="949df-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="949df-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="949df-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="949df-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="949df-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="949df-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="949df-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="949df-119">The call timed out.</span></span>|  
|<span data-ttu-id="949df-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="949df-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="949df-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="949df-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="949df-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="949df-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="949df-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="949df-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="949df-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="949df-124">E_FAIL</span></span>|<span data-ttu-id="949df-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="949df-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="949df-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="949df-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="949df-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="949df-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="949df-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="949df-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="949df-129">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="949df-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="949df-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="949df-130">Remarks</span></span>  
 <span data-ttu-id="949df-131">CLR [IHostMemoryManager:: Createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir [IHostMAlloc](ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="949df-131">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="949df-132">`DebugAlloc`çalışma zamanının hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="949df-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949df-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="949df-133">Requirements</span></span>  
 <span data-ttu-id="949df-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="949df-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="949df-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="949df-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="949df-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="949df-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="949df-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="949df-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949df-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="949df-138">See also</span></span>

- [<span data-ttu-id="949df-139">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="949df-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="949df-140">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="949df-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
