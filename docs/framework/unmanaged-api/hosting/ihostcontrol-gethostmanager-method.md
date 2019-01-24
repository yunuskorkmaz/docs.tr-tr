---
title: IHostControl::GetHostManager Metodu
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 821968fbde6d3f5434b83adf8c9661fe39d96293
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742035"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="d89b9-102">IHostControl::GetHostManager Metodu</span><span class="sxs-lookup"><span data-stu-id="d89b9-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="d89b9-103">Ana bilgisayarın uygulanmasına arabirimi belirtilen bir arabirim işaretçisi alır `IID`.</span><span class="sxs-lookup"><span data-stu-id="d89b9-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d89b9-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d89b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d89b9-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="d89b9-106">[in] `IID` Ortak dil çalışma zamanı (CLR) için sorgulama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d89b9-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d89b9-107">[out] Konak uygulanan arabirimi ya da konak bu arabirimi desteklemiyorsa null bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d89b9-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d89b9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d89b9-108">Return Value</span></span>  
  
|<span data-ttu-id="d89b9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d89b9-109">HRESULT</span></span>|<span data-ttu-id="d89b9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d89b9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d89b9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d89b9-111">S_OK</span></span>|<span data-ttu-id="d89b9-112">`GetHostManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d89b9-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="d89b9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d89b9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d89b9-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d89b9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d89b9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d89b9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d89b9-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d89b9-116">The call timed out.</span></span>|  
|<span data-ttu-id="d89b9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d89b9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d89b9-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d89b9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d89b9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d89b9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d89b9-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d89b9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d89b9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d89b9-121">E_FAIL</span></span>|<span data-ttu-id="d89b9-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d89b9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d89b9-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d89b9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d89b9-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d89b9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d89b9-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d89b9-125">E_INVALIDARG</span></span>|<span data-ttu-id="d89b9-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d89b9-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="d89b9-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d89b9-127">E_NOINTERFACE</span></span>|<span data-ttu-id="d89b9-128">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d89b9-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d89b9-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d89b9-129">Remarks</span></span>  
 <span data-ttu-id="d89b9-130">CLR bir veya daha fazla aşağıdaki arabirimlerinden destekleyip desteklemediğini belirlemek üzere konak sorgular:</span><span class="sxs-lookup"><span data-stu-id="d89b9-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="d89b9-131">Ihostmemorymanager</span><span class="sxs-lookup"><span data-stu-id="d89b9-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="d89b9-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="d89b9-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="d89b9-140">Konak belirtilen arabirim destekliyorsa, bu ayarlar `ppObject` bu arabirimi uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="d89b9-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="d89b9-141">Aksi takdirde ayarlar `ppObject` null.</span><span class="sxs-lookup"><span data-stu-id="d89b9-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="d89b9-142">CLR çağrılmayan `Release` konak yöneticileri bile bunu kapattığınızda, şirket.</span><span class="sxs-lookup"><span data-stu-id="d89b9-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89b9-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d89b9-143">Requirements</span></span>  
 <span data-ttu-id="d89b9-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d89b9-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89b9-145">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d89b9-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d89b9-146">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d89b9-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d89b9-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89b9-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89b9-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d89b9-148">See also</span></span>
- [<span data-ttu-id="d89b9-149">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89b9-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
