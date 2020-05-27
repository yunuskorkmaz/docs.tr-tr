---
title: IHostMAlloc::Alloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: 6f58e2290afa166d48306c0bbb50edd1df36888b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804640"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="9d13e-102">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d13e-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="9d13e-103">Konağın yığından belirtilen bellek miktarını ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="9d13e-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d13e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9d13e-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d13e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d13e-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="9d13e-106">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9d13e-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="9d13e-107">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="9d13e-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="9d13e-108">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="9d13e-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d13e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9d13e-109">Return Value</span></span>  
  
|<span data-ttu-id="9d13e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d13e-110">HRESULT</span></span>|<span data-ttu-id="9d13e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d13e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d13e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d13e-112">S_OK</span></span>|<span data-ttu-id="9d13e-113">`Alloc`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9d13e-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="9d13e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d13e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d13e-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9d13e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d13e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d13e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d13e-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9d13e-117">The call timed out.</span></span>|  
|<span data-ttu-id="9d13e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d13e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d13e-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d13e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d13e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d13e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d13e-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9d13e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d13e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d13e-122">E_FAIL</span></span>|<span data-ttu-id="9d13e-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9d13e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d13e-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9d13e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d13e-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d13e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d13e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9d13e-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9d13e-127">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="9d13e-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d13e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d13e-128">Remarks</span></span>  
 <span data-ttu-id="9d13e-129">CLR, `IHostMalloc` [IHostMemoryManager:: createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9d13e-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d13e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d13e-130">Requirements</span></span>  
 <span data-ttu-id="9d13e-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d13e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d13e-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d13e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d13e-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9d13e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d13e-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d13e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d13e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d13e-135">See also</span></span>

- [<span data-ttu-id="9d13e-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d13e-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="9d13e-137">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d13e-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
