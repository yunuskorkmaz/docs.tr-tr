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
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762532"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="81d96-102">ICLRRuntimeInfo::IsLoaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81d96-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="81d96-103">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma ZAMANıNıN (CLR) bir işleme yüklenip yüklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="81d96-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="81d96-104">Çalışma zamanı, aynı zamanda başlatılmadan de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="81d96-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d96-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="81d96-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d96-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81d96-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="81d96-107">'ndaki İşlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="81d96-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="81d96-108">[out] `true` CLR işleme yüklenirse, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="81d96-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81d96-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81d96-109">Return Value</span></span>  
 <span data-ttu-id="81d96-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="81d96-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="81d96-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81d96-111">HRESULT</span></span>|<span data-ttu-id="81d96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81d96-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81d96-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="81d96-113">S_OK</span></span>|<span data-ttu-id="81d96-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="81d96-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="81d96-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="81d96-115">E_POINTER</span></span>|<span data-ttu-id="81d96-116">`pbLoaded`null.</span><span class="sxs-lookup"><span data-stu-id="81d96-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d96-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81d96-117">Remarks</span></span>  
 <span data-ttu-id="81d96-118">Bu yöntem, aşağıdaki işlevler ve arabirimler ile geriye dönük olarak uyumludur:</span><span class="sxs-lookup"><span data-stu-id="81d96-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="81d96-119">[ICorRuntimeHost](icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="81d96-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="81d96-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimi (.NET Framework 2,0 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="81d96-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="81d96-121">Kullanım dışı bırakılan `CorBindTo*` işlevler (bkz. .NET Framework 2,0 barındırma API 'Sindeki [kullanım dışı clr barındırma işlevleri](deprecated-clr-hosting-functions.md) ).</span><span class="sxs-lookup"><span data-stu-id="81d96-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="81d96-122">Bir ana bilgisayar, `CorBindTo*` clr 'nin belirli bir sürümünü oluşturmak Için [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) işlevi gibi kullanım dışı işlevlerden birini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="81d96-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="81d96-123">Konak daha sonra [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metodunu çağırabilir ve bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi elde etmek için aynı sürüm numarasını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="81d96-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="81d96-124">Daha sonra ana bilgisayar `IsLoaded` döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimindeki yöntemi çağırırsa `pbLoaded` `true` ; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="81d96-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d96-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81d96-125">Requirements</span></span>  
 <span data-ttu-id="81d96-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d96-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d96-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="81d96-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="81d96-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="81d96-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81d96-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d96-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d96-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81d96-130">See also</span></span>

- [<span data-ttu-id="81d96-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81d96-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="81d96-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="81d96-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="81d96-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="81d96-133">Hosting</span></span>](index.md)
