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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133772"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="c3b36-102">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3b36-102">LockClrVersion Function</span></span>
<span data-ttu-id="c3b36-103">Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c3b36-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="c3b36-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3b36-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3b36-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="c3b36-107">'ndaki Başlatma sonrasında CLR tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b36-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="c3b36-108">'ndaki Başlatmanın başladığı CLR 'yi bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b36-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="c3b36-109">'ndaki Başlatma işleminin tamamlandığını CLR bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b36-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3b36-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3b36-110">Return Value</span></span>  
 <span data-ttu-id="c3b36-111">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3b36-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c3b36-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c3b36-112">Return code</span></span>|<span data-ttu-id="c3b36-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3b36-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c3b36-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3b36-114">S_OK</span></span>|<span data-ttu-id="c3b36-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c3b36-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="c3b36-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3b36-116">E_INVALIDARG</span></span>|<span data-ttu-id="c3b36-117">Bağımsız değişkenlerden biri veya birkaçı null.</span><span class="sxs-lookup"><span data-stu-id="c3b36-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3b36-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3b36-118">Remarks</span></span>  
 <span data-ttu-id="c3b36-119">Konak, CLR 'yi başlatmadan önce `LockClrVersion` çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="c3b36-120">`LockClrVersion`, tümü [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="c3b36-121">Bu tür aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="c3b36-122">Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:</span><span class="sxs-lookup"><span data-stu-id="c3b36-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="c3b36-123">Konak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="c3b36-124">Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="c3b36-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="c3b36-125">Çalışma zamanı, `hostCallback` parametresi tarafından belirtilen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3b36-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="c3b36-126">`hostCallback` tarafından belirtilen işlev, aşağıdaki çağrı dizisini yapar:</span><span class="sxs-lookup"><span data-stu-id="c3b36-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="c3b36-127">`pBeginHostSetup` parametresi tarafından belirtilen işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b36-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="c3b36-128">`CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="c3b36-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="c3b36-129">[ICLRRuntimeHost:: SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3b36-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="c3b36-130">[ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3b36-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="c3b36-131">`pEndHostSetup` parametresi tarafından belirtilen işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b36-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="c3b36-132">`pEndHostSetup` `pBeginHostSetup` olan tüm çağrılar, aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c3b36-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="c3b36-133">Bu iş parçacığı `hostCallback` çağrıldığı iş parçacığından farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3b36-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b36-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3b36-134">Requirements</span></span>  
 <span data-ttu-id="c3b36-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b36-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b36-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3b36-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3b36-137">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3b36-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3b36-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b36-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b36-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b36-139">See also</span></span>

- [<span data-ttu-id="c3b36-140">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c3b36-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
