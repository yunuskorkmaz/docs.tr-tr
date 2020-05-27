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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008501"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="9209c-102">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="9209c-102">LockClrVersion Function</span></span>
<span data-ttu-id="9209c-103">Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9209c-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="9209c-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9209c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9209c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9209c-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9209c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9209c-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="9209c-107">'ndaki Başlatma sonrasında CLR tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="9209c-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="9209c-108">'ndaki Başlatmanın başladığı CLR 'yi bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="9209c-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="9209c-109">'ndaki Başlatma işleminin tamamlandığını CLR bilgilendirmek için konak tarafından çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="9209c-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9209c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9209c-110">Return Value</span></span>  
 <span data-ttu-id="9209c-111">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9209c-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9209c-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="9209c-112">Return code</span></span>|<span data-ttu-id="9209c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9209c-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9209c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9209c-114">S_OK</span></span>|<span data-ttu-id="9209c-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9209c-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="9209c-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9209c-116">E_INVALIDARG</span></span>|<span data-ttu-id="9209c-117">Bağımsız değişkenlerden biri veya birkaçı null.</span><span class="sxs-lookup"><span data-stu-id="9209c-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9209c-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9209c-118">Remarks</span></span>  
 <span data-ttu-id="9209c-119">CLR başlatmadan önce konak çağırır `LockClrVersion` .</span><span class="sxs-lookup"><span data-stu-id="9209c-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="9209c-120">`LockClrVersion`tümü [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır.</span><span class="sxs-lookup"><span data-stu-id="9209c-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="9209c-121">Bu tür aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9209c-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="9209c-122">Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:</span><span class="sxs-lookup"><span data-stu-id="9209c-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="9209c-123">Konak [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9209c-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="9209c-124">Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="9209c-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="9209c-125">Çalışma zamanı, parametresi tarafından belirtilen işlevi çağırır `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="9209c-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="9209c-126">Daha sonra belirtilen işlev `hostCallback` aşağıdaki çağrı dizisini yapar:</span><span class="sxs-lookup"><span data-stu-id="9209c-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="9209c-127">Parametresi tarafından belirtilen işlev `pBeginHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="9209c-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="9209c-128">`CorBindToRuntimeEx`(veya başka bir çalışma zamanı başlatma işlevi).</span><span class="sxs-lookup"><span data-stu-id="9209c-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="9209c-129">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="9209c-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="9209c-130">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="9209c-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="9209c-131">Parametresi tarafından belirtilen işlev `pEndHostSetup` .</span><span class="sxs-lookup"><span data-stu-id="9209c-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="9209c-132">' Den ' e yapılan tüm çağrılar, `pBeginHostSetup` `pEndHostSetup` aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="9209c-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="9209c-133">Bu iş parçacığı, üzerinde çağrılan iş parçacığından farklı olabilir `hostCallback` .</span><span class="sxs-lookup"><span data-stu-id="9209c-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9209c-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9209c-134">Requirements</span></span>  
 <span data-ttu-id="9209c-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9209c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9209c-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9209c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9209c-137">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9209c-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9209c-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9209c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9209c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9209c-139">See also</span></span>

- [<span data-ttu-id="9209c-140">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9209c-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
