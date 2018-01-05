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
ms.workload: dotnet
ms.openlocfilehash: 4775b6ae00f34d7d046515f8700a35470b2f6650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="3fad1-102">IHostMAlloc::Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fad1-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="3fad1-103">Kullanarak ayrılmış bellek boşaltır [ayırma](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="3fad1-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fad1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fad1-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fad1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fad1-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="3fad1-106">[in] Boşaltılacak belleğin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3fad1-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fad1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3fad1-107">Return Value</span></span>  
  
|<span data-ttu-id="3fad1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fad1-108">HRESULT</span></span>|<span data-ttu-id="3fad1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fad1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fad1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fad1-110">S_OK</span></span>|<span data-ttu-id="3fad1-111">`Free`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3fad1-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="3fad1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fad1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fad1-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3fad1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fad1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fad1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fad1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3fad1-115">The call timed out.</span></span>|  
|<span data-ttu-id="3fad1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fad1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fad1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3fad1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fad1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fad1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fad1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3fad1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fad1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fad1-120">E_FAIL</span></span>|<span data-ttu-id="3fad1-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3fad1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fad1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3fad1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fad1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fad1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3fad1-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3fad1-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3fad1-125">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="3fad1-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fad1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fad1-126">Remarks</span></span>  
 <span data-ttu-id="3fad1-127">Varsa `pMem` parametresi için bir çağrı kullanılarak ayrılmamış bellek bölgesi başvurduğu `Alloc`, konak HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fad1-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fad1-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fad1-128">Requirements</span></span>  
 <span data-ttu-id="3fad1-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fad1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fad1-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3fad1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fad1-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3fad1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fad1-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fad1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fad1-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fad1-133">See Also</span></span>  
 [<span data-ttu-id="3fad1-134">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fad1-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="3fad1-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fad1-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
