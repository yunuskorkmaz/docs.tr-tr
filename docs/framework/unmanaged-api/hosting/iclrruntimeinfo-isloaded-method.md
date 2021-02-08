---
description: ': ICLRRuntimeInfo:: IsLoaded Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e6a5984dbd2340fe07af546dd48ae6760d5b4271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799713"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="d1c30-103">ICLRRuntimeInfo::IsLoaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1c30-103">ICLRRuntimeInfo::IsLoaded Method</span></span>

<span data-ttu-id="d1c30-104">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma ZAMANıNıN (CLR) bir işleme yüklenip yüklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1c30-104">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="d1c30-105">Çalışma zamanı, aynı zamanda başlatılmadan de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c30-105">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c30-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1c30-106">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1c30-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1c30-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="d1c30-108">'ndaki İşlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="d1c30-108">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="d1c30-109">[out] `true` CLR işleme yüklenirse, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="d1c30-109">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1c30-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1c30-110">Return Value</span></span>  

 <span data-ttu-id="d1c30-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1c30-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d1c30-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1c30-112">HRESULT</span></span>|<span data-ttu-id="d1c30-113">Description</span><span class="sxs-lookup"><span data-stu-id="d1c30-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1c30-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1c30-114">S_OK</span></span>|<span data-ttu-id="d1c30-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d1c30-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="d1c30-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d1c30-116">E_POINTER</span></span>|<span data-ttu-id="d1c30-117">`pbLoaded` null.</span><span class="sxs-lookup"><span data-stu-id="d1c30-117">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1c30-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1c30-118">Remarks</span></span>  

 <span data-ttu-id="d1c30-119">Bu yöntem, aşağıdaki işlevler ve arabirimler ile geriye dönük olarak uyumludur:</span><span class="sxs-lookup"><span data-stu-id="d1c30-119">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="d1c30-120">[ICorRuntimeHost](icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="d1c30-120">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="d1c30-121">[ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimi (.NET Framework 2,0 barındırma API 'si).</span><span class="sxs-lookup"><span data-stu-id="d1c30-121">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="d1c30-122">Kullanım dışı bırakılan `CorBindTo*` işlevler (bkz. .NET Framework 2,0 barındırma API 'Sindeki [kullanım dışı clr barındırma işlevleri](deprecated-clr-hosting-functions.md) ).</span><span class="sxs-lookup"><span data-stu-id="d1c30-122">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="d1c30-123">Bir ana bilgisayar, `CorBindTo*` clr 'nin belirli bir sürümünü oluşturmak Için [CorBindToRuntime](corbindtoruntime-function.md) işlevi gibi kullanım dışı işlevlerden birini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c30-123">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="d1c30-124">Konak daha sonra [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) metodunu çağırabilir ve bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi elde etmek için aynı sürüm numarasını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c30-124">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="d1c30-125">Daha sonra ana bilgisayar `IsLoaded` döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimindeki yöntemi çağırırsa `pbLoaded` `true` ; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="d1c30-125">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c30-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1c30-126">Requirements</span></span>  

 <span data-ttu-id="d1c30-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c30-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c30-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d1c30-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d1c30-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d1c30-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1c30-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c30-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c30-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c30-131">See also</span></span>

- [<span data-ttu-id="d1c30-132">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1c30-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d1c30-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1c30-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d1c30-134">Hosting</span><span class="sxs-lookup"><span data-stu-id="d1c30-134">Hosting</span></span>](index.md)
