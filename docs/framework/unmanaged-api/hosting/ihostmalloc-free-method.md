---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cf60d4e711d0c88b5fb8b4c213b19bdea564324
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477835"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="c3bc0-102">IHostMAlloc::Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3bc0-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="c3bc0-103">Kullanarak ayrılan bellek serbest bırakma [ayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3bc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3bc0-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3bc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3bc0-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="c3bc0-106">[in] Serbest bırakılacak bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3bc0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3bc0-107">Return Value</span></span>  
  
|<span data-ttu-id="c3bc0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3bc0-108">HRESULT</span></span>|<span data-ttu-id="c3bc0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3bc0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3bc0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3bc0-110">S_OK</span></span>|<span data-ttu-id="c3bc0-111">`Free` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="c3bc0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3bc0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3bc0-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3bc0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3bc0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3bc0-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-115">The call timed out.</span></span>|  
|<span data-ttu-id="c3bc0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3bc0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3bc0-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3bc0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3bc0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3bc0-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3bc0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3bc0-120">E_FAIL</span></span>|<span data-ttu-id="c3bc0-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3bc0-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3bc0-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c3bc0-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c3bc0-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c3bc0-125">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3bc0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3bc0-126">Remarks</span></span>  
 <span data-ttu-id="c3bc0-127">Varsa `pMem` parametresi için bir çağrı kullanılarak ayrılmamış bir bellek bölgesini başvurduğu `Alloc`, konak HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3bc0-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3bc0-128">Requirements</span></span>  
 <span data-ttu-id="c3bc0-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3bc0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3bc0-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3bc0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3bc0-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c3bc0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3bc0-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3bc0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3bc0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3bc0-133">See also</span></span>
- [<span data-ttu-id="c3bc0-134">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3bc0-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="c3bc0-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3bc0-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
