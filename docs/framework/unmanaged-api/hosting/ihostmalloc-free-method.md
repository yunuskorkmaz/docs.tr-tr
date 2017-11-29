---
title: "IHostMAlloc::Free Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Free
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ac361f939a134aa6d2bc8b215c5d447b352466e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="05010-102">IHostMAlloc::Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05010-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="05010-103">Kullanarak ayrılmış bellek boşaltır [ayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="05010-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05010-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05010-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05010-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="05010-106">[in] Boşaltılacak belleğin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05010-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05010-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05010-107">Return Value</span></span>  
  
|<span data-ttu-id="05010-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05010-108">HRESULT</span></span>|<span data-ttu-id="05010-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05010-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05010-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="05010-110">S_OK</span></span>|<span data-ttu-id="05010-111">`Free`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05010-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="05010-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05010-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05010-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="05010-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05010-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05010-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05010-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="05010-115">The call timed out.</span></span>|  
|<span data-ttu-id="05010-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05010-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05010-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="05010-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05010-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05010-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05010-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="05010-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05010-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05010-120">E_FAIL</span></span>|<span data-ttu-id="05010-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="05010-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05010-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05010-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05010-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="05010-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="05010-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="05010-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="05010-125">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="05010-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05010-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05010-126">Remarks</span></span>  
 <span data-ttu-id="05010-127">Varsa `pMem` parametresi için bir çağrı kullanılarak ayrılmamış bellek bölgesi başvurduğu `Alloc`, konak HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="05010-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05010-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05010-128">Requirements</span></span>  
 <span data-ttu-id="05010-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05010-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05010-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05010-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05010-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="05010-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05010-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05010-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05010-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05010-133">See Also</span></span>  
 [<span data-ttu-id="05010-134">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="05010-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="05010-135">Ihostmalloc arabirimi</span><span class="sxs-lookup"><span data-stu-id="05010-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
