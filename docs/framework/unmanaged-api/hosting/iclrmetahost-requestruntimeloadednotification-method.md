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
ms.openlocfilehash: 539f69c33b67ad1a8a514062c5d777deaced1599
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965000"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="d9b63-102">ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9b63-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="d9b63-103">Ortak dil çalışma zamanı (CLR) sürümü ilk kez yüklendiğinde, ancak henüz başlamamışsa çağrılan bir geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b63-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="d9b63-104">Bu yöntem [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="d9b63-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b63-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9b63-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b63-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9b63-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="d9b63-107">'ndaki Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.</span><span class="sxs-lookup"><span data-stu-id="d9b63-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9b63-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9b63-108">Return Value</span></span>  
 <span data-ttu-id="d9b63-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9b63-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d9b63-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9b63-110">HRESULT</span></span>|<span data-ttu-id="d9b63-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9b63-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9b63-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9b63-112">S_OK</span></span>|<span data-ttu-id="d9b63-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d9b63-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d9b63-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d9b63-114">E_POINTER</span></span>|<span data-ttu-id="d9b63-115">`pCallbackFunction`null.</span><span class="sxs-lookup"><span data-stu-id="d9b63-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9b63-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9b63-116">Remarks</span></span>  
 <span data-ttu-id="d9b63-117">Geri çağırma aşağıdaki şekilde işe yarar:</span><span class="sxs-lookup"><span data-stu-id="d9b63-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="d9b63-118">Geri çağırma yalnızca bir çalışma zamanı ilk kez yüklendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9b63-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="d9b63-119">Aynı çalışma zamanının yer aldığı yük yükleri için geri çağırma çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d9b63-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="d9b63-120">Yer suz çalışma zamanı yükleri için geri çağırma işlevine yapılan çağrılar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d9b63-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="d9b63-121">Geri çağırma işlevi aşağıdaki prototiple sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d9b63-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="d9b63-122">Geri çağırma işlevi prototipleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d9b63-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="d9b63-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="d9b63-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="d9b63-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="d9b63-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="d9b63-125">Ana bilgisayar yüklemeyi amaçlıyordu veya başka bir çalışma zamanının `pfnCallbackThreadSet` yeniden eklenen bir şekilde yüklenmesine neden olursa, geri çağırma işlevinde belirtilen ve `pfnCallbackThreadUnset` parametreleri aşağıdaki şekilde kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d9b63-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="d9b63-126">`pfnCallbackThreadSet`Bu tür bir yük denenerek çalışma zamanı yüküne neden olabilecek iş parçacığı tarafından çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9b63-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="d9b63-127">`pfnCallbackThreadUnset`iş parçacığı artık böyle bir çalışma zamanı yüküne (ve ilk geri aramadan dönmeden önce) neden olmaz çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9b63-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="d9b63-128">`pfnCallbackThreadSet`ve `pfnCallbackThreadUnset` her ikisi de yer yok.</span><span class="sxs-lookup"><span data-stu-id="d9b63-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9b63-129">Konak uygulamalar, `pfnCallbackThreadSet` `pfnCallbackThreadUnset` parametre`pCallbackFunction` kapsamını çağırmamalıdır ve dışarıda olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9b63-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b63-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9b63-130">Requirements</span></span>  
 <span data-ttu-id="d9b63-131">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b63-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b63-132">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d9b63-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9b63-133">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d9b63-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b63-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b63-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b63-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b63-135">See also</span></span>

- [<span data-ttu-id="d9b63-136">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9b63-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d9b63-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9b63-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
