---
description: ': LockClrVersion Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 268c08cdd24a826ba92cc8865dfd036f544febcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679933"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="f3a0b-103">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f3a0b-103">LockClrVersion Function</span></span>

<span data-ttu-id="f3a0b-104">Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-104">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="f3a0b-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a0b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3a0b-106">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3a0b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3a0b-107">Parameters</span></span>  

 `hostCallback`  
 <span data-ttu-id="f3a0b-108">'ndaki Başlatma sonrasında CLR tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-108">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="f3a0b-109">'ndaki Başlatmanın başladığı CLR 'yi bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-109">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="f3a0b-110">'ndaki Başlatma işleminin tamamlandığını CLR bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-110">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3a0b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3a0b-111">Return Value</span></span>  

 <span data-ttu-id="f3a0b-112">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-112">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f3a0b-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f3a0b-113">Return code</span></span>|<span data-ttu-id="f3a0b-114">Description</span><span class="sxs-lookup"><span data-stu-id="f3a0b-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f3a0b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3a0b-115">S_OK</span></span>|<span data-ttu-id="f3a0b-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="f3a0b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f3a0b-117">E_INVALIDARG</span></span>|<span data-ttu-id="f3a0b-118">Bağımsız değişkenlerden biri veya birkaçı null.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-118">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a0b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3a0b-119">Remarks</span></span>  

 <span data-ttu-id="f3a0b-120">CLR başlatmadan önce konak çağırır `LockClrVersion` .</span><span class="sxs-lookup"><span data-stu-id="f3a0b-120">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="f3a0b-121">`LockClrVersion` tümü [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-121">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="f3a0b-122">Bu tür aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-122">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="f3a0b-123">Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:</span><span class="sxs-lookup"><span data-stu-id="f3a0b-123">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="f3a0b-124">Konak [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-124">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="f3a0b-125">Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-125">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="f3a0b-126">Çalışma zamanı, parametresi tarafından belirtilen işlevi çağırır `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="f3a0b-126">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="f3a0b-127">Daha sonra belirtilen işlev `hostCallback` aşağıdaki çağrı dizisini yapar:</span><span class="sxs-lookup"><span data-stu-id="f3a0b-127">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="f3a0b-128">Parametresi tarafından belirtilen işlev `pBeginHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="f3a0b-128">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="f3a0b-129">`CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="f3a0b-129">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="f3a0b-130">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3a0b-130">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="f3a0b-131">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3a0b-131">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="f3a0b-132">Parametresi tarafından belirtilen işlev `pEndHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="f3a0b-132">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="f3a0b-133">' Den ' e yapılan tüm çağrılar, `pBeginHostSetup` `pEndHostSetup` aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-133">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="f3a0b-134">Bu iş parçacığı, üzerinde çağrılan iş parçacığından farklı olabilir `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="f3a0b-134">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a0b-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3a0b-135">Requirements</span></span>  

 <span data-ttu-id="f3a0b-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a0b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a0b-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3a0b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3a0b-138">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3a0b-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3a0b-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a0b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a0b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3a0b-140">See also</span></span>

- [<span data-ttu-id="f3a0b-141">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f3a0b-141">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
