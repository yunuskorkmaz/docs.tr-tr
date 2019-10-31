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
ms.openlocfilehash: 23f868bba2dc058d99f1c5c09e9b311b1ff3634a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140895"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="dda0e-102">ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dda0e-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="dda0e-103">Ortak dil çalışma zamanı (CLR) sürümü ilk kez yüklendiğinde, ancak henüz başlamamışsa çağrılan bir geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda0e-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="dda0e-104">Bu yöntem [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="dda0e-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda0e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dda0e-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda0e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dda0e-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="dda0e-107">'ndaki Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.</span><span class="sxs-lookup"><span data-stu-id="dda0e-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda0e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dda0e-108">Return Value</span></span>  
 <span data-ttu-id="dda0e-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="dda0e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dda0e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dda0e-110">HRESULT</span></span>|<span data-ttu-id="dda0e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dda0e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dda0e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dda0e-112">S_OK</span></span>|<span data-ttu-id="dda0e-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="dda0e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="dda0e-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="dda0e-114">E_POINTER</span></span>|<span data-ttu-id="dda0e-115">`pCallbackFunction` null.</span><span class="sxs-lookup"><span data-stu-id="dda0e-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dda0e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dda0e-116">Remarks</span></span>  
 <span data-ttu-id="dda0e-117">Geri çağırma aşağıdaki şekilde işe yarar:</span><span class="sxs-lookup"><span data-stu-id="dda0e-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="dda0e-118">Geri çağırma yalnızca bir çalışma zamanı ilk kez yüklendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="dda0e-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="dda0e-119">Aynı çalışma zamanının yer aldığı yük yükleri için geri çağırma çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="dda0e-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="dda0e-120">Yer suz çalışma zamanı yükleri için geri çağırma işlevine yapılan çağrılar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dda0e-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="dda0e-121">Geri çağırma işlevi aşağıdaki prototiple sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dda0e-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="dda0e-122">Geri çağırma işlevi prototipleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dda0e-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="dda0e-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="dda0e-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="dda0e-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="dda0e-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="dda0e-125">Ana bilgisayar yüklemeyi amaçlıyordu veya başka bir çalışma zamanının yeniden eklenen bir şekilde yüklenmesine neden olursa, geri arama işlevinde belirtilen `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` parametreleri aşağıdaki şekilde kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="dda0e-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="dda0e-126">`pfnCallbackThreadSet`, bir yük denenerek çalışma zamanı yüküne neden olabilecek iş parçacığı tarafından çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dda0e-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="dda0e-127">iş parçacığı artık böyle bir çalışma zamanı yüküne (ve ilk geri aramadan dönmeden önce) neden olmaz, `pfnCallbackThreadUnset` çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dda0e-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="dda0e-128">`pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` her ikisi de yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dda0e-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dda0e-129">Ana bilgisayar uygulamaları `pfnCallbackThreadSet` ve `pCallbackFunction` parametresinin kapsamı dışında `pfnCallbackThreadUnset` çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="dda0e-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda0e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dda0e-130">Requirements</span></span>  
 <span data-ttu-id="dda0e-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda0e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda0e-132">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="dda0e-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dda0e-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="dda0e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dda0e-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda0e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda0e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda0e-135">See also</span></span>

- [<span data-ttu-id="dda0e-136">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda0e-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="dda0e-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="dda0e-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
