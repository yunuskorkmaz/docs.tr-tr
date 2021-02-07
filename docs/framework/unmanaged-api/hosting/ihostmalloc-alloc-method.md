---
description: 'Şu konuda daha fazla bilgi edinin: IHostMAlloc:: ayırma yöntemi'
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
ms.openlocfilehash: e0349c273ef9e3194bb8bad167510dd8fefcab62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708245"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="e9448-103">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9448-103">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="e9448-104">Konağın yığından belirtilen bellek miktarını ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="e9448-104">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9448-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9448-105">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9448-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9448-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="e9448-107">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e9448-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="e9448-108">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="e9448-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="e9448-109">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="e9448-109">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9448-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9448-110">Return Value</span></span>  
  
|<span data-ttu-id="e9448-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9448-111">HRESULT</span></span>|<span data-ttu-id="e9448-112">Description</span><span class="sxs-lookup"><span data-stu-id="e9448-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9448-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9448-113">S_OK</span></span>|<span data-ttu-id="e9448-114">`Alloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9448-114">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="e9448-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9448-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9448-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e9448-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9448-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9448-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9448-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9448-118">The call timed out.</span></span>|  
|<span data-ttu-id="e9448-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9448-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9448-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e9448-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9448-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9448-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9448-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e9448-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9448-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9448-123">E_FAIL</span></span>|<span data-ttu-id="e9448-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9448-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9448-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9448-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9448-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9448-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9448-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e9448-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e9448-128">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="e9448-128">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9448-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9448-129">Remarks</span></span>  

 <span data-ttu-id="e9448-130">CLR, `IHostMalloc` [IHostMemoryManager:: createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e9448-130">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9448-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9448-131">Requirements</span></span>  

 <span data-ttu-id="e9448-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9448-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9448-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e9448-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9448-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e9448-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9448-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9448-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9448-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9448-136">See also</span></span>

- [<span data-ttu-id="e9448-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9448-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="e9448-138">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9448-138">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
