---
title: "LockClrVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be41ae47f78a41e2f2be10a1e38d938dde9a4701
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lockclrversion-function"></a><span data-ttu-id="6b6fb-102">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6b6fb-102">LockClrVersion Function</span></span>
<span data-ttu-id="6b6fb-103">CLR açıkça başlatmadan önce işlemi içinde ortak dil çalışma zamanı (CLR) hangi sürümünün kullanılacağını belirlemek için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="6b6fb-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b6fb-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6fb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b6fb-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b6fb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b6fb-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="6b6fb-107">[in] Başlatma sırasında CLR tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="6b6fb-108">[in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="6b6fb-109">[in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b6fb-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b6fb-110">Return Value</span></span>  
 <span data-ttu-id="6b6fb-111">Bu yöntem standart COM hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="6b6fb-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="6b6fb-112">Return code</span></span>|<span data-ttu-id="6b6fb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b6fb-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6b6fb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b6fb-114">S_OK</span></span>|<span data-ttu-id="6b6fb-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b6fb-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6b6fb-116">E_INVALIDARG</span></span>|<span data-ttu-id="6b6fb-117">Bir veya daha fazla bağımsız değişken null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b6fb-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b6fb-118">Remarks</span></span>  
 <span data-ttu-id="6b6fb-119">Ana bilgisayar çağrıları `LockClrVersion` CLR başlatma önce.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="6b6fb-120">`LockClrVersion`tümü geri aramalar türü üç parametre alır [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="6b6fb-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="6b6fb-121">Bu tür şu şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="6b6fb-122">Aşağıdaki adımlar, çalışma zamanı modülü başlatma sırasında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="6b6fb-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="6b6fb-123">Ana bilgisayar çağrıları [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya bir çalışma zamanı başlatma işlevleri biri.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="6b6fb-124">Alternatif olarak, konak COM Nesne etkinleştirmesi kullanarak çalışma zamanı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="6b6fb-125">Çalışma zamanı tarafından belirtilen işlevi çağırır `hostCallback` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="6b6fb-126">Tarafından belirtilen işlevin `hostCallback` çağrıları aşağıdaki dizisi hale getirir:</span><span class="sxs-lookup"><span data-stu-id="6b6fb-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="6b6fb-127">Tarafından belirtilen işlevin `pBeginHostSetup` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="6b6fb-128">`CorBindToRuntimeEx`(veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="6b6fb-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="6b6fb-129">[Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="6b6fb-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="6b6fb-130">[Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="6b6fb-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="6b6fb-131">Tarafından belirtilen işlevin `pEndHostSetup` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="6b6fb-132">Gelen tüm çağrıları `pBeginHostSetup` için `pEndHostSetup` tek iş parçacığı veya fiber aynı mantıksal yığınına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="6b6fb-133">Bu iş parçacığı iş parçacığı üzerine farklı olabilir `hostCallback` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b6fb-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b6fb-134">Requirements</span></span>  
 <span data-ttu-id="6b6fb-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b6fb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b6fb-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b6fb-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b6fb-137">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b6fb-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b6fb-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b6fb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6fb-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b6fb-139">See Also</span></span>  
 [<span data-ttu-id="6b6fb-140">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="6b6fb-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
