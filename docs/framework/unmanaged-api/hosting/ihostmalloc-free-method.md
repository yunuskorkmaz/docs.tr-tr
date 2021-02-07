---
description: 'Şu konuda daha fazla bilgi edinin: IHostMAlloc:: Free yöntemi'
title: IHostMAlloc::Free Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 097e2e95b6dfb9d6a1bae68f9e0455a96383159e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708209"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="a004d-103">IHostMAlloc::Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a004d-103">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="a004d-104">[Ayırma](ihostmalloc-alloc-method.md) işlevi kullanılarak ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a004d-104">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a004d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a004d-105">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a004d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a004d-106">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="a004d-107">'ndaki Boşaltılacak belleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a004d-107">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a004d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a004d-108">Return Value</span></span>  
  
|<span data-ttu-id="a004d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a004d-109">HRESULT</span></span>|<span data-ttu-id="a004d-110">Description</span><span class="sxs-lookup"><span data-stu-id="a004d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a004d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a004d-111">S_OK</span></span>|<span data-ttu-id="a004d-112">`Free` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a004d-112">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="a004d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a004d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a004d-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a004d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a004d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a004d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a004d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a004d-116">The call timed out.</span></span>|  
|<span data-ttu-id="a004d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a004d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a004d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a004d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a004d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a004d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a004d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a004d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a004d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a004d-121">E_FAIL</span></span>|<span data-ttu-id="a004d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a004d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a004d-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a004d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a004d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a004d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a004d-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a004d-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a004d-126">Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="a004d-126">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a004d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a004d-127">Remarks</span></span>  

 <span data-ttu-id="a004d-128">Parametresi, `pMem` çağrısı kullanılarak ayrılmamış bir bellek bölgesine başvuruyorsa `Alloc` , ana bilgisayar HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="a004d-128">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a004d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a004d-129">Requirements</span></span>  

 <span data-ttu-id="a004d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a004d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a004d-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a004d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a004d-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a004d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a004d-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a004d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a004d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a004d-134">See also</span></span>

- [<span data-ttu-id="a004d-135">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a004d-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="a004d-136">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a004d-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
