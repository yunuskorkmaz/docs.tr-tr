---
title: LockClrVersion İşlevi
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3b263efa95936190ed771e811a84886b11be75b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465758"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="5c0e3-102">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="5c0e3-102">LockClrVersion Function</span></span>
<span data-ttu-id="5c0e3-103">Ortak dil çalışma zamanı (CLR) hangi sürümünün işlem dahilinde CLR açıkça başlatılmadan önce kullanılacağını belirlemek için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="5c0e3-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c0e3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0e3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c0e3-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c0e3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c0e3-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="5c0e3-107">[in] CLR başlatma sırasında tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="5c0e3-108">[in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="5c0e3-109">[in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c0e3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c0e3-110">Return Value</span></span>  
 <span data-ttu-id="5c0e3-111">Bu yöntem, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5c0e3-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="5c0e3-112">Return code</span></span>|<span data-ttu-id="5c0e3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c0e3-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5c0e3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c0e3-114">S_OK</span></span>|<span data-ttu-id="5c0e3-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="5c0e3-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5c0e3-116">E_INVALIDARG</span></span>|<span data-ttu-id="5c0e3-117">Bir veya daha fazla bağımsız değişken NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c0e3-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c0e3-118">Remarks</span></span>  
 <span data-ttu-id="5c0e3-119">Konak çağrıları `LockClrVersion` CLR başlatma önce.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="5c0e3-120">`LockClrVersion` geri çağırmaları türünün her biri, üç parametre almayan [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="5c0e3-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="5c0e3-121">Bu tür şu şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="5c0e3-122">Aşağıdaki adımlar, çalışma zamanı başlatma sırasında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="5c0e3-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="5c0e3-123">Konak çağrıları [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya bir çalışma zamanı başlatma işlevlerden biri.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="5c0e3-124">Alternatif olarak, konak COM Nesne etkinleştirmesi kullanarak çalışma zamanı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="5c0e3-125">Çalışma zamanı tarafından belirtilen işlev çağrıları `hostCallback` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="5c0e3-126">Tarafından belirtilen işlevin `hostCallback` sonra sırasıyla aşağıdaki çağrıları yapar:</span><span class="sxs-lookup"><span data-stu-id="5c0e3-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="5c0e3-127">Tarafından belirtilen işlevin `pBeginHostSetup` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="5c0e3-128">`CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="5c0e3-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="5c0e3-129">[Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c0e3-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="5c0e3-130">[Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c0e3-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="5c0e3-131">Tarafından belirtilen işlevin `pEndHostSetup` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="5c0e3-132">Tüm çağrıların `pBeginHostSetup` için `pEndHostSetup` tek iş parçacığı veya aynı mantıksal yığınına sahip bir fiber gerçekleşmemelidir.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="5c0e3-133">Bu iş parçacığının iş parçacığı alacağı farklı `hostCallback` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c0e3-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c0e3-134">Requirements</span></span>  
 <span data-ttu-id="5c0e3-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c0e3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c0e3-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c0e3-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c0e3-137">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c0e3-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c0e3-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c0e3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0e3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c0e3-139">See also</span></span>
- [<span data-ttu-id="5c0e3-140">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5c0e3-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
