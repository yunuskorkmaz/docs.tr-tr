---
title: IHostControl::GetHostManager Yöntemi
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
ms.openlocfilehash: cad7b319a20bce09779821af6f50aea086880c26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968330"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="3c8ff-102">IHostControl::GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c8ff-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="3c8ff-103">Ana bilgisayarın uygulanmasına arabirimi belirtilen bir arabirim işaretçisi alır `IID`.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c8ff-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c8ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c8ff-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="3c8ff-106">[in] `IID` Ortak dil çalışma zamanı (CLR) için sorgulama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="3c8ff-107">[out] Konak uygulanan arabirimi ya da konak bu arabirimi desteklemiyorsa null bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c8ff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c8ff-108">Return Value</span></span>  
  
|<span data-ttu-id="3c8ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c8ff-109">HRESULT</span></span>|<span data-ttu-id="3c8ff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c8ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c8ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c8ff-111">S_OK</span></span>|<span data-ttu-id="3c8ff-112">`GetHostManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="3c8ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c8ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c8ff-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c8ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c8ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c8ff-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="3c8ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c8ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c8ff-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c8ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c8ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c8ff-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c8ff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c8ff-121">E_FAIL</span></span>|<span data-ttu-id="3c8ff-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c8ff-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c8ff-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3c8ff-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3c8ff-125">E_INVALIDARG</span></span>|<span data-ttu-id="3c8ff-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="3c8ff-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="3c8ff-127">E_NOINTERFACE</span></span>|<span data-ttu-id="3c8ff-128">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c8ff-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c8ff-129">Remarks</span></span>  
 <span data-ttu-id="3c8ff-130">CLR bir veya daha fazla aşağıdaki arabirimlerinden destekleyip desteklemediğini belirlemek üzere konak sorgular:</span><span class="sxs-lookup"><span data-stu-id="3c8ff-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="3c8ff-131">Ihostmemorymanager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="3c8ff-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="3c8ff-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="3c8ff-140">Konak belirtilen arabirim destekliyorsa, bu ayarlar `ppObject` bu arabirimi uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="3c8ff-141">Aksi takdirde ayarlar `ppObject` null.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="3c8ff-142">CLR çağrılmayan `Release` konak yöneticileri bile bunu kapattığınızda, şirket.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c8ff-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c8ff-143">Requirements</span></span>  
 <span data-ttu-id="3c8ff-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c8ff-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8ff-145">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c8ff-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c8ff-146">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3c8ff-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c8ff-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c8ff-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8ff-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c8ff-148">See also</span></span>

- [<span data-ttu-id="3c8ff-149">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c8ff-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
