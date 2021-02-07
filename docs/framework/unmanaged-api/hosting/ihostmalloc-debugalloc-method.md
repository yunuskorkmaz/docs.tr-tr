---
description: 'Şu konuda daha fazla bilgi edinin: IHostMAlloc::D ebugAlloc yöntemi'
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
ms.openlocfilehash: f94ff0d6cc1e25daee12c67c38167f7f14829510
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708222"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="c14ed-103">IHostMAlloc::DebugAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c14ed-103">IHostMAlloc::DebugAlloc Method</span></span>

<span data-ttu-id="c14ed-104">Konağın yığından belirtilen miktarda bellek ayırmasını ve ayrıca belleğin nerede ayrıldığını izlemelerini ister.</span><span class="sxs-lookup"><span data-stu-id="c14ed-104">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c14ed-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c14ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c14ed-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="c14ed-107">'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c14ed-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="c14ed-108">'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](ememorycriticallevel-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c14ed-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="c14ed-109">'ndaki Hata ayıklanan yürütülebilir dosyanın kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="c14ed-109">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="c14ed-110">'ndaki Ayırmanın istendiği satır numarası `pszFileName` .</span><span class="sxs-lookup"><span data-stu-id="c14ed-110">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="c14ed-111">dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.</span><span class="sxs-lookup"><span data-stu-id="c14ed-111">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c14ed-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c14ed-112">Return Value</span></span>  
  
|<span data-ttu-id="c14ed-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c14ed-113">HRESULT</span></span>|<span data-ttu-id="c14ed-114">Description</span><span class="sxs-lookup"><span data-stu-id="c14ed-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c14ed-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c14ed-115">S_OK</span></span>|<span data-ttu-id="c14ed-116">`DebugAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c14ed-116">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="c14ed-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c14ed-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c14ed-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c14ed-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c14ed-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c14ed-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c14ed-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c14ed-120">The call timed out.</span></span>|  
|<span data-ttu-id="c14ed-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c14ed-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c14ed-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c14ed-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c14ed-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c14ed-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c14ed-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c14ed-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c14ed-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c14ed-125">E_FAIL</span></span>|<span data-ttu-id="c14ed-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c14ed-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c14ed-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c14ed-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c14ed-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c14ed-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c14ed-129">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c14ed-129">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c14ed-130">Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="c14ed-130">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c14ed-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c14ed-131">Remarks</span></span>  

 <span data-ttu-id="c14ed-132">CLR [IHostMemoryManager:: Createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir [IHostMAlloc](ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c14ed-132">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="c14ed-133">`DebugAlloc` çalışma zamanının hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c14ed-133">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c14ed-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c14ed-134">Requirements</span></span>  

 <span data-ttu-id="c14ed-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14ed-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c14ed-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c14ed-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c14ed-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c14ed-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c14ed-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c14ed-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14ed-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c14ed-139">See also</span></span>

- [<span data-ttu-id="c14ed-140">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c14ed-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="c14ed-141">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c14ed-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
