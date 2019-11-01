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
ms.openlocfilehash: 9837e4e3428a0293c8e689b3f3e081aa07f055b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192077"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="369b6-102">IHostMAlloc::Alloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369b6-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="369b6-103">Konağın yığından belirtilen bellek miktarını ayırmasını ister.</span><span class="sxs-lookup"><span data-stu-id="369b6-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="369b6-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="369b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="369b6-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="369b6-106">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="369b6-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="369b6-107">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="369b6-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="369b6-108">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="369b6-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="369b6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="369b6-109">Return Value</span></span>  
  
|<span data-ttu-id="369b6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="369b6-110">HRESULT</span></span>|<span data-ttu-id="369b6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369b6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="369b6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="369b6-112">S_OK</span></span>|<span data-ttu-id="369b6-113">`Alloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="369b6-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="369b6-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="369b6-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="369b6-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="369b6-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="369b6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="369b6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="369b6-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="369b6-117">The call timed out.</span></span>|  
|<span data-ttu-id="369b6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="369b6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="369b6-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="369b6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="369b6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="369b6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="369b6-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="369b6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="369b6-122">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="369b6-122">E_FAIL</span></span>|<span data-ttu-id="369b6-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="369b6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="369b6-124">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="369b6-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="369b6-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="369b6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="369b6-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="369b6-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="369b6-127">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="369b6-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="369b6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="369b6-128">Remarks</span></span>  
 <span data-ttu-id="369b6-129">CLR, [IHostMemoryManager:: Createmayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir `IHostMalloc` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="369b6-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="369b6-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="369b6-130">Requirements</span></span>  
 <span data-ttu-id="369b6-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="369b6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="369b6-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="369b6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="369b6-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="369b6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="369b6-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="369b6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369b6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="369b6-135">See also</span></span>

- [<span data-ttu-id="369b6-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="369b6-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="369b6-137">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="369b6-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
