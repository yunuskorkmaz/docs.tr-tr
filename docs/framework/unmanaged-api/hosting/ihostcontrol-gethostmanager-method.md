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
ms.openlocfilehash: 25e931ec17cad3508d548fb4ca7e53b0ade3f119
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804963"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="80fab-102">IHostControl::GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80fab-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="80fab-103">Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="80fab-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="80fab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80fab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80fab-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="80fab-106">'ndaki `IID`Ortak dil çalışma zamanının (CLR) sorguladığını belirten arabirim.</span><span class="sxs-lookup"><span data-stu-id="80fab-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="80fab-107">dışı Konak tarafından uygulanan arabirime yönelik bir işaretçi veya konak bu arabirimi desteklemiyorsa NULL.</span><span class="sxs-lookup"><span data-stu-id="80fab-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80fab-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80fab-108">Return Value</span></span>  
  
|<span data-ttu-id="80fab-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80fab-109">HRESULT</span></span>|<span data-ttu-id="80fab-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80fab-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80fab-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80fab-111">S_OK</span></span>|<span data-ttu-id="80fab-112">`GetHostManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="80fab-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="80fab-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80fab-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80fab-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="80fab-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80fab-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80fab-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80fab-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="80fab-116">The call timed out.</span></span>|  
|<span data-ttu-id="80fab-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80fab-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80fab-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="80fab-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80fab-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80fab-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80fab-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="80fab-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80fab-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80fab-121">E_FAIL</span></span>|<span data-ttu-id="80fab-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="80fab-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80fab-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="80fab-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80fab-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="80fab-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80fab-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="80fab-125">E_INVALIDARG</span></span>|<span data-ttu-id="80fab-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="80fab-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="80fab-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="80fab-127">E_NOINTERFACE</span></span>|<span data-ttu-id="80fab-128">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="80fab-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80fab-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80fab-129">Remarks</span></span>  
 <span data-ttu-id="80fab-130">CLR, aşağıdaki arabirimlerden birini veya birkaçını destekleyip desteklemediğini öğrenmek için Konağı sorgular:</span><span class="sxs-lookup"><span data-stu-id="80fab-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="80fab-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="80fab-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="80fab-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="80fab-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="80fab-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="80fab-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="80fab-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="80fab-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="80fab-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="80fab-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="80fab-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="80fab-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="80fab-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="80fab-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="80fab-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="80fab-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="80fab-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="80fab-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="80fab-140">Ana bilgisayar belirtilen arabirimi destekliyorsa, `ppObject` Bu arabirimin uygulamasına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80fab-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="80fab-141">Aksi halde, `ppObject` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80fab-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="80fab-142">Siz `Release` kapatsanız bile, clr konak yöneticilerinde çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="80fab-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80fab-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80fab-143">Requirements</span></span>  
 <span data-ttu-id="80fab-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80fab-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80fab-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80fab-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80fab-146">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="80fab-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80fab-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80fab-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80fab-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80fab-148">See also</span></span>

- [<span data-ttu-id="80fab-149">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80fab-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
