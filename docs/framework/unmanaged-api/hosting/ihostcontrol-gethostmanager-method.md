---
title: IHostControl::GetHostManager Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.GetHostManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c711fb2ddf5d21cd8e122a35ebd0b8a5ce0e752f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="3fda6-102">IHostControl::GetHostManager Metodu</span><span class="sxs-lookup"><span data-stu-id="3fda6-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="3fda6-103">Arabirim işaretçisi arabirimi ana bilgisayarın uygulaması için belirtilen alır `IID`.</span><span class="sxs-lookup"><span data-stu-id="3fda6-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fda6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fda6-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fda6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fda6-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="3fda6-106">[in] `IID` Ortak dil çalışma zamanı (CLR) için sorgulama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3fda6-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="3fda6-107">[out] Ana bilgisayar uygulanan arabirimi ya da ana bilgisayar bu arabirim desteklemiyorsa null işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3fda6-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fda6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3fda6-108">Return Value</span></span>  
  
|<span data-ttu-id="3fda6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fda6-109">HRESULT</span></span>|<span data-ttu-id="3fda6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fda6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fda6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fda6-111">S_OK</span></span>|<span data-ttu-id="3fda6-112">`GetHostManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3fda6-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="3fda6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fda6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fda6-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3fda6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fda6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fda6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fda6-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3fda6-116">The call timed out.</span></span>|  
|<span data-ttu-id="3fda6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fda6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fda6-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3fda6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fda6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fda6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fda6-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3fda6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fda6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fda6-121">E_FAIL</span></span>|<span data-ttu-id="3fda6-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3fda6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fda6-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3fda6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fda6-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fda6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3fda6-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3fda6-125">E_INVALIDARG</span></span>|<span data-ttu-id="3fda6-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3fda6-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="3fda6-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="3fda6-127">E_NOINTERFACE</span></span>|<span data-ttu-id="3fda6-128">İstenen arabirimi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="3fda6-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fda6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fda6-129">Remarks</span></span>  
 <span data-ttu-id="3fda6-130">CLR bir veya daha fazla aşağıdaki arabirimleri destekleyip desteklemediğini belirlemek için ana sorgular:</span><span class="sxs-lookup"><span data-stu-id="3fda6-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="3fda6-131">Ihostmemorymanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-132">Ihosttaskmanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-133">Ihostthreadpoolmanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-134">Ihostıocompletionmanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-135">Ihostsyncmanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-136">Ihostassemblymanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-137">Ihostgcmanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-138">Ihostpolicymanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="3fda6-139">Ihostsecuritymanager</span><span class="sxs-lookup"><span data-stu-id="3fda6-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="3fda6-140">Konak belirtilen arabirim destekliyorsa, ayarlar `ppObject` bu arabirimin uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="3fda6-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="3fda6-141">Aksi takdirde, ayarlar `ppObject` null.</span><span class="sxs-lookup"><span data-stu-id="3fda6-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="3fda6-142">CLR çağrılmayan `Release` bile, kapattığınızda konak yöneticilere.</span><span class="sxs-lookup"><span data-stu-id="3fda6-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fda6-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fda6-143">Requirements</span></span>  
 <span data-ttu-id="3fda6-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fda6-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fda6-145">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3fda6-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fda6-146">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3fda6-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fda6-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fda6-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fda6-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fda6-148">See Also</span></span>  
 [<span data-ttu-id="3fda6-149">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fda6-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
