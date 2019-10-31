---
title: ICLRRuntimeInfo::IsLoaded Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: e0ab16348abbaff00152f2b259ccafdd331174df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136355"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="5ecd5-102">ICLRRuntimeInfo::IsLoaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ecd5-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="5ecd5-103">[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma ZAMANıNıN (CLR) bir işleme yüklenip yüklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="5ecd5-104">Çalışma zamanı, aynı zamanda başlatılmadan de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ecd5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ecd5-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ecd5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ecd5-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="5ecd5-107">'ndaki İşlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="5ecd5-108">[out] CLR işleme yüklenirse `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ecd5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ecd5-109">Return Value</span></span>  
 <span data-ttu-id="5ecd5-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5ecd5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ecd5-111">HRESULT</span></span>|<span data-ttu-id="5ecd5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ecd5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ecd5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ecd5-113">S_OK</span></span>|<span data-ttu-id="5ecd5-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5ecd5-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5ecd5-115">E_POINTER</span></span>|<span data-ttu-id="5ecd5-116">`pbLoaded` null.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ecd5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ecd5-117">Remarks</span></span>  
 <span data-ttu-id="5ecd5-118">Bu yöntem, aşağıdaki işlevler ve arabirimler ile geriye dönük olarak uyumludur:</span><span class="sxs-lookup"><span data-stu-id="5ecd5-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="5ecd5-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="5ecd5-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="5ecd5-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi (.NET Framework 2,0 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="5ecd5-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="5ecd5-121">Kullanım dışı `CorBindTo*` işlevleri (bkz. .NET Framework 2,0 barındırma API 'sindeki [kullanım DıŞı clr barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) ).</span><span class="sxs-lookup"><span data-stu-id="5ecd5-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="5ecd5-122">Bir konak, CLR 'nin belirli bir sürümünü oluşturmak için [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) işlevi gibi kullanım dışı `CorBindTo*` işlevlerinden birini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="5ecd5-123">Konak daha sonra [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metodunu çağırabilir ve bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi elde etmek için aynı sürüm numarasını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="5ecd5-124">Daha sonra ana bilgisayar döndürülen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimindeki `IsLoaded` yöntemini çağırırsa `pbLoaded` `true`döndürür; Aksi takdirde, `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ecd5-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ecd5-125">Requirements</span></span>  
 <span data-ttu-id="5ecd5-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ecd5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ecd5-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5ecd5-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5ecd5-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5ecd5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ecd5-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ecd5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecd5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ecd5-130">See also</span></span>

- [<span data-ttu-id="5ecd5-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ecd5-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5ecd5-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ecd5-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5ecd5-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="5ecd5-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
