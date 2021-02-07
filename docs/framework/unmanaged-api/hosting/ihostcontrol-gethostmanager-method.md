---
description: ': IHostControl:: GetHostManager yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7cc118808c8788504da2cc07a8c61c419d3c588f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708916"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="f6c11-103">IHostControl::GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6c11-103">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="f6c11-104">Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="f6c11-104">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c11-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6c11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6c11-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6c11-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="f6c11-107">'ndaki `IID` Ortak dil çalışma zamanının (CLR) sorguladığını belirten arabirim.</span><span class="sxs-lookup"><span data-stu-id="f6c11-107">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f6c11-108">dışı Konak tarafından uygulanan arabirime yönelik bir işaretçi veya konak bu arabirimi desteklemiyorsa NULL.</span><span class="sxs-lookup"><span data-stu-id="f6c11-108">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6c11-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f6c11-109">Return Value</span></span>  
  
|<span data-ttu-id="f6c11-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6c11-110">HRESULT</span></span>|<span data-ttu-id="f6c11-111">Description</span><span class="sxs-lookup"><span data-stu-id="f6c11-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6c11-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6c11-112">S_OK</span></span>|<span data-ttu-id="f6c11-113">`GetHostManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f6c11-113">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="f6c11-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6c11-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6c11-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f6c11-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6c11-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6c11-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6c11-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f6c11-117">The call timed out.</span></span>|  
|<span data-ttu-id="f6c11-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6c11-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6c11-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f6c11-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6c11-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6c11-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6c11-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f6c11-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6c11-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6c11-122">E_FAIL</span></span>|<span data-ttu-id="f6c11-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f6c11-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6c11-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f6c11-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6c11-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6c11-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f6c11-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f6c11-126">E_INVALIDARG</span></span>|<span data-ttu-id="f6c11-127">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f6c11-127">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="f6c11-128">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="f6c11-128">E_NOINTERFACE</span></span>|<span data-ttu-id="f6c11-129">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f6c11-129">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6c11-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6c11-130">Remarks</span></span>  

 <span data-ttu-id="f6c11-131">CLR, aşağıdaki arabirimlerden birini veya birkaçını destekleyip desteklemediğini öğrenmek için Konağı sorgular:</span><span class="sxs-lookup"><span data-stu-id="f6c11-131">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="f6c11-132">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-132">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="f6c11-133">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-133">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="f6c11-134">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-134">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="f6c11-135">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-135">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="f6c11-136">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-136">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="f6c11-137">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-137">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="f6c11-138">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-138">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="f6c11-139">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-139">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="f6c11-140">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="f6c11-140">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="f6c11-141">Ana bilgisayar belirtilen arabirimi destekliyorsa, `ppObject` Bu arabirimin uygulamasına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6c11-141">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="f6c11-142">Aksi halde, `ppObject` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6c11-142">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="f6c11-143">Siz `Release` kapatsanız bile, clr konak yöneticilerinde çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="f6c11-143">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c11-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6c11-144">Requirements</span></span>  

 <span data-ttu-id="f6c11-145">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c11-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c11-146">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f6c11-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6c11-147">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f6c11-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6c11-148">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c11-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c11-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6c11-149">See also</span></span>

- [<span data-ttu-id="f6c11-150">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6c11-150">IHostControl Interface</span></span>](ihostcontrol-interface.md)
