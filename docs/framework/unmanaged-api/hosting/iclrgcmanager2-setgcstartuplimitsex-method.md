---
title: "ICLRGCManager2::SetGCStartupLimitsEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73f5678008354b312964f0cb32d768d36a641fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="440cd-102">ICLRGCManager2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="440cd-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="440cd-103">Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.</span><span class="sxs-lookup"><span data-stu-id="440cd-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="440cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="440cd-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="440cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="440cd-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="440cd-106">[in] Çöp toplama kesim belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="440cd-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="440cd-107">Minimum kesim boyutu 4 MB'tır.</span><span class="sxs-lookup"><span data-stu-id="440cd-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="440cd-108">Kesimleri artan aralıklarla 1 MB veya daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="440cd-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="440cd-109">[in] 0 oluşturma için belirtilen en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="440cd-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="440cd-110">Minimum kuşak 0 boyutu 64 KB'tır.</span><span class="sxs-lookup"><span data-stu-id="440cd-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="440cd-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="440cd-111">Return Value</span></span>  
  
|<span data-ttu-id="440cd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="440cd-112">HRESULT</span></span>|<span data-ttu-id="440cd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="440cd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="440cd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="440cd-114">S_OK</span></span>|<span data-ttu-id="440cd-115">`SetGCStartupLimitsEx`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="440cd-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="440cd-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="440cd-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="440cd-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="440cd-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="440cd-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="440cd-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="440cd-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="440cd-119">The call timed out.</span></span>|  
|<span data-ttu-id="440cd-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="440cd-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="440cd-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="440cd-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="440cd-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="440cd-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="440cd-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="440cd-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="440cd-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="440cd-124">E_FAIL</span></span>|<span data-ttu-id="440cd-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="440cd-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="440cd-126">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="440cd-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="440cd-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="440cd-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="440cd-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="440cd-128">Remarks</span></span>  
 <span data-ttu-id="440cd-129">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="440cd-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="440cd-130">Daha sonra çağrılar `SetGCStartupLimitsEx` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="440cd-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="440cd-131">Her iki parametre diğer etkilemeden ayarlamak için değiştirmek istemiyorsanız parametresi için 0 (sıfır) belirtin.</span><span class="sxs-lookup"><span data-stu-id="440cd-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="440cd-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="440cd-132">Requirements</span></span>  
 <span data-ttu-id="440cd-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="440cd-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="440cd-134">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="440cd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="440cd-135">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="440cd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="440cd-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="440cd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="440cd-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="440cd-137">See Also</span></span>  
 [<span data-ttu-id="440cd-138">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="440cd-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="440cd-139">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="440cd-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="440cd-140">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="440cd-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="440cd-141">Iclrgcmanager2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="440cd-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
