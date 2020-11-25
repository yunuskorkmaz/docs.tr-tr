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
ms.openlocfilehash: 2ff08ec8f194ccc9e968b3a7ee017afe788f4b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704948"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="f52f7-102">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f52f7-102">LockClrVersion Function</span></span>

<span data-ttu-id="f52f7-103">Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f52f7-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="f52f7-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f52f7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52f7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f52f7-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f52f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f52f7-106">Parameters</span></span>  

 `hostCallback`  
 <span data-ttu-id="f52f7-107">'ndaki Başlatma sonrasında CLR tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f52f7-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="f52f7-108">'ndaki Başlatmanın başladığı CLR 'yi bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f52f7-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="f52f7-109">'ndaki Başlatma işleminin tamamlandığını CLR bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f52f7-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f52f7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f52f7-110">Return Value</span></span>  

 <span data-ttu-id="f52f7-111">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f52f7-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f52f7-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f52f7-112">Return code</span></span>|<span data-ttu-id="f52f7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f52f7-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f52f7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f52f7-114">S_OK</span></span>|<span data-ttu-id="f52f7-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f52f7-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f52f7-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f52f7-116">E_INVALIDARG</span></span>|<span data-ttu-id="f52f7-117">Bağımsız değişkenlerden biri veya birkaçı null.</span><span class="sxs-lookup"><span data-stu-id="f52f7-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f52f7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f52f7-118">Remarks</span></span>  

 <span data-ttu-id="f52f7-119">CLR başlatmadan önce konak çağırır `LockClrVersion` .</span><span class="sxs-lookup"><span data-stu-id="f52f7-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="f52f7-120">`LockClrVersion` tümü [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f52f7-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="f52f7-121">Bu tür aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f52f7-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="f52f7-122">Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:</span><span class="sxs-lookup"><span data-stu-id="f52f7-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="f52f7-123">Konak [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f52f7-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="f52f7-124">Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="f52f7-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="f52f7-125">Çalışma zamanı, parametresi tarafından belirtilen işlevi çağırır `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="f52f7-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="f52f7-126">Daha sonra belirtilen işlev `hostCallback` aşağıdaki çağrı dizisini yapar:</span><span class="sxs-lookup"><span data-stu-id="f52f7-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="f52f7-127">Parametresi tarafından belirtilen işlev `pBeginHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="f52f7-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="f52f7-128">`CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="f52f7-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="f52f7-129">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="f52f7-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="f52f7-130">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="f52f7-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="f52f7-131">Parametresi tarafından belirtilen işlev `pEndHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="f52f7-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="f52f7-132">' Den ' e yapılan tüm çağrılar, `pBeginHostSetup` `pEndHostSetup` aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f52f7-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="f52f7-133">Bu iş parçacığı, üzerinde çağrılan iş parçacığından farklı olabilir `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="f52f7-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f52f7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f52f7-134">Requirements</span></span>  

 <span data-ttu-id="f52f7-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f52f7-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f52f7-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f52f7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f52f7-137">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f52f7-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f52f7-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f52f7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52f7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f52f7-139">See also</span></span>

- [<span data-ttu-id="f52f7-140">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f52f7-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
