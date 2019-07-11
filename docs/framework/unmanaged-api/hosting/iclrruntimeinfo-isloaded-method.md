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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7eafd9c3c9eeb14e53643bed09309ca8d3b5855
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748436"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="6b984-102">ICLRRuntimeInfo::IsLoaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b984-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="6b984-103">Ortak dil çalışma zamanı (CLR) ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi, işlem içine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6b984-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="6b984-104">Bir çalışma zamanı ayrıca başlatılmadan yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6b984-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b984-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b984-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b984-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b984-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="6b984-107">[in] İşlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="6b984-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="6b984-108">[out] `true` CLR'yi işlem içine yüklenmiş; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="6b984-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b984-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b984-109">Return Value</span></span>  
 <span data-ttu-id="6b984-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="6b984-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b984-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b984-111">HRESULT</span></span>|<span data-ttu-id="6b984-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b984-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b984-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b984-113">S_OK</span></span>|<span data-ttu-id="6b984-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6b984-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b984-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6b984-115">E_POINTER</span></span>|<span data-ttu-id="6b984-116">`pbLoaded` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="6b984-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b984-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b984-117">Remarks</span></span>  
 <span data-ttu-id="6b984-118">Geriye dönük olarak uyumlu bu yöntem aşağıdaki işlevler ve arabirimleri ile:</span><span class="sxs-lookup"><span data-stu-id="6b984-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="6b984-119">[Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabiriminde (.NET Framework sürüm 1 barındırma API'si).</span><span class="sxs-lookup"><span data-stu-id="6b984-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="6b984-120">[Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi (API barındırma .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="6b984-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="6b984-121">Kullanım dışı `CorBindTo*` işlevleri (bkz [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API'sini barındıran .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="6b984-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="6b984-122">Bir konak kullanım dışı birini çağırabilir `CorBindTo*` gibi işlevler [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) CLR'nin belirli bir sürümünü oluşturmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="6b984-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="6b984-123">Konak sonra çağırabilirsiniz [Iclrmetahost::getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi ve almak için aynı sürüm numarasını belirtin bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6b984-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="6b984-124">Konak çağırıyorsa `IsLoaded` yöntemi döndürülen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi `pbLoaded` döndürür `true`; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="6b984-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b984-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b984-125">Requirements</span></span>  
 <span data-ttu-id="6b984-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b984-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b984-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6b984-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6b984-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6b984-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b984-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b984-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b984-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b984-130">See also</span></span>

- [<span data-ttu-id="6b984-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b984-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6b984-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6b984-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6b984-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="6b984-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
