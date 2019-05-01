---
title: ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61fce3e06b5245872f7061716e8d995dd5f5043c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984652"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="e1c55-102">ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1c55-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="e1c55-103">Bir ortak dil çalışma zamanı (CLR) sürümünü ilk yüklendi, ancak henüz başlatılmadı çağrılacak garantili bir geri çağırma işlevini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c55-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="e1c55-104">Bu yöntem yerine geçer [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="e1c55-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1c55-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c55-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c55-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="e1c55-107">[in] Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.</span><span class="sxs-lookup"><span data-stu-id="e1c55-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1c55-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1c55-108">Return Value</span></span>  
 <span data-ttu-id="e1c55-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e1c55-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1c55-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1c55-110">HRESULT</span></span>|<span data-ttu-id="e1c55-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1c55-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1c55-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1c55-112">S_OK</span></span>|<span data-ttu-id="e1c55-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e1c55-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e1c55-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e1c55-114">E_POINTER</span></span>|<span data-ttu-id="e1c55-115">`pCallbackFunction` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="e1c55-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c55-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1c55-116">Remarks</span></span>  
 <span data-ttu-id="e1c55-117">Geri çağırma şu şekilde çalışır:</span><span class="sxs-lookup"><span data-stu-id="e1c55-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="e1c55-118">Geri çağırma yalnızca bir çalışma zamanı ilk kez yüklendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e1c55-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="e1c55-119">Geri çağırma desteklemeyeceğini aynı çalışma zamanı yükler için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="e1c55-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="e1c55-120">Reentrant olmayan çalışma zamanı yükler için geri çağırma işlevi için çağrı serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="e1c55-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="e1c55-121">Geri çağırma işlevine aşağıdaki prototip sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e1c55-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="e1c55-122">Geri arama işlev prototipleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e1c55-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="e1c55-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="e1c55-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="e1c55-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="e1c55-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="e1c55-125">Konak yüklenemiyor veya yeniden girilen bir biçimde yüklenmesi başka bir çalışma zamanı neden planlıyorsa `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` geri aramada işlevi aşağıdaki şekilde kullanılmalıdır. sağlanan parametre:</span><span class="sxs-lookup"><span data-stu-id="e1c55-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="e1c55-126">`pfnCallbackThreadSet` Böyle bir yük denenmeden önce bir çalışma zamanı yükleme neden olabilecek bir iş parçacığı tarafından çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1c55-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="e1c55-127">`pfnCallbackThreadUnset` iş parçacığı artık böyle bir çalışma zamanı yükleme neden olur (ve ilk geri çağrısından döndürerek önce) çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1c55-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="e1c55-128">`pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` reentrant olmayan olduğunda.</span><span class="sxs-lookup"><span data-stu-id="e1c55-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1c55-129">Ana bilgisayar uygulamaları gerekir çağrılmayan `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` kapsamı dışında `pCallbackFunction` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e1c55-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c55-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1c55-130">Requirements</span></span>  
 <span data-ttu-id="e1c55-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c55-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c55-132">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e1c55-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1c55-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e1c55-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1c55-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c55-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c55-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c55-135">See also</span></span>

- [<span data-ttu-id="e1c55-136">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c55-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="e1c55-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e1c55-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
