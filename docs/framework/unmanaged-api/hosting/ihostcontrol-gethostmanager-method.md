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
ms.openlocfilehash: c23773dce448c8c98d4926dff3fa51100e683fd0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192045"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="f9e7d-102">IHostControl::GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9e7d-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="f9e7d-103">Ana bilgisayarın, belirtilen `IID`sahip olduğu arabirim uygulamasına yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9e7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9e7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9e7d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="f9e7d-106">'ndaki Ortak dil çalışma zamanının (CLR) sorgulamakta olduğu arabirimin `IID`.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f9e7d-107">dışı Konak tarafından uygulanan arabirime yönelik bir işaretçi veya konak bu arabirimi desteklemiyorsa NULL.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e7d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9e7d-108">Return Value</span></span>  
  
|<span data-ttu-id="f9e7d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9e7d-109">HRESULT</span></span>|<span data-ttu-id="f9e7d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9e7d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9e7d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9e7d-111">S_OK</span></span>|<span data-ttu-id="f9e7d-112">`GetHostManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="f9e7d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9e7d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9e7d-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9e7d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9e7d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9e7d-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9e7d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9e7d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9e7d-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9e7d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9e7d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9e7d-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9e7d-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="f9e7d-121">E_FAIL</span></span>|<span data-ttu-id="f9e7d-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9e7d-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9e7d-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9e7d-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9e7d-125">E_INVALIDARG</span></span>|<span data-ttu-id="f9e7d-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="f9e7d-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="f9e7d-127">E_NOINTERFACE</span></span>|<span data-ttu-id="f9e7d-128">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9e7d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9e7d-129">Remarks</span></span>  
 <span data-ttu-id="f9e7d-130">CLR, aşağıdaki arabirimlerden birini veya birkaçını destekleyip desteklemediğini öğrenmek için Konağı sorgular:</span><span class="sxs-lookup"><span data-stu-id="f9e7d-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="f9e7d-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="f9e7d-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="f9e7d-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="f9e7d-140">Ana bilgisayar belirtilen arabirimi destekliyorsa, bu arabirimin uygulamasına `ppObject` ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="f9e7d-141">Aksi takdirde, `ppObject` null olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="f9e7d-142">CLR, siz kapatsanız bile konak yöneticilerinde `Release` çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e7d-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9e7d-143">Requirements</span></span>  
 <span data-ttu-id="f9e7d-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e7d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e7d-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9e7d-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9e7d-146">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f9e7d-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9e7d-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e7d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e7d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9e7d-148">See also</span></span>

- [<span data-ttu-id="f9e7d-149">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9e7d-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
