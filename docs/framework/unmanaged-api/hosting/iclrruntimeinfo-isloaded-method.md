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
ms.openlocfilehash: 7615f5dad1666685333011503c5bef4c98a6a8bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771689"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="7c81a-102">ICLRRuntimeInfo::IsLoaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c81a-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="7c81a-103">Ortak dil çalışma zamanı (CLR) ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi, işlem içine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7c81a-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="7c81a-104">Bir çalışma zamanı ayrıca başlatılmadan yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7c81a-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c81a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c81a-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c81a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c81a-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="7c81a-107">[in] İşlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7c81a-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="7c81a-108">[out] `true` CLR'yi işlem içine yüklenmiş; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="7c81a-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c81a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7c81a-109">Return Value</span></span>  
 <span data-ttu-id="7c81a-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="7c81a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7c81a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c81a-111">HRESULT</span></span>|<span data-ttu-id="7c81a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c81a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c81a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c81a-113">S_OK</span></span>|<span data-ttu-id="7c81a-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7c81a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7c81a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7c81a-115">E_POINTER</span></span>|<span data-ttu-id="7c81a-116">`pbLoaded` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="7c81a-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c81a-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c81a-117">Remarks</span></span>  
 <span data-ttu-id="7c81a-118">Geriye dönük olarak uyumlu bu yöntem aşağıdaki işlevler ve arabirimleri ile:</span><span class="sxs-lookup"><span data-stu-id="7c81a-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="7c81a-119">[Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabiriminde (.NET Framework sürüm 1 barındırma API'si).</span><span class="sxs-lookup"><span data-stu-id="7c81a-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="7c81a-120">[Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi (API barındırma .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="7c81a-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="7c81a-121">Kullanım dışı `CorBindTo*` işlevleri (bkz [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API'sini barındıran .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="7c81a-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="7c81a-122">Bir konak kullanım dışı birini çağırabilir `CorBindTo*` gibi işlevler [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) CLR'nin belirli bir sürümünü oluşturmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="7c81a-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="7c81a-123">Konak sonra çağırabilirsiniz [Iclrmetahost::getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi ve almak için aynı sürüm numarasını belirtin bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7c81a-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="7c81a-124">Konak çağırıyorsa `IsLoaded` yöntemi döndürülen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi `pbLoaded` döndürür `true`; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="7c81a-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c81a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c81a-125">Requirements</span></span>  
 <span data-ttu-id="7c81a-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c81a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c81a-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7c81a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7c81a-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7c81a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c81a-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c81a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c81a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c81a-130">See also</span></span>

- [<span data-ttu-id="7c81a-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c81a-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7c81a-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c81a-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7c81a-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7c81a-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
