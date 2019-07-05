---
title: ICLRMetaHost::GetRuntime Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 004122e9bb52dfe2e51ca00cd5362b2b7a06f30e
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569569"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="8bd51-102">ICLRMetaHost::GetRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="8bd51-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="8bd51-103">Alır [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ortak dil çalışma zamanı (CLR) belirli bir sürümüne karşılık gelen arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8bd51-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="8bd51-104">Bu yöntem yerine geçer [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ile kullanılan işlev [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="8bd51-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd51-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bd51-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bd51-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bd51-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="8bd51-107">[in] .NET Framework derleme sürümü biçiminde meta verilerde depolanan "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="8bd51-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="8bd51-108">*A*, *B*, ve *X* ana sürüm, ikincil sürüm ve derleme numarasını karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="8bd51-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bd51-109">C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64 altında göründüğü gibi bu parametre .NET Framework sürümü için dizin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8bd51-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="8bd51-110">Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *X*"burada *X* yüklü derleme sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8bd51-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="8bd51-111">"V" ön eki gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8bd51-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="8bd51-112">[in] İstendiği arayüz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8bd51-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="8bd51-113">Şu anda, bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo ' dir.</span><span class="sxs-lookup"><span data-stu-id="8bd51-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="8bd51-114">[out] Bir işaretçi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) istenen çalışma zamanı için karşılık gelen arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8bd51-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bd51-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8bd51-115">Return Value</span></span>  
 <span data-ttu-id="8bd51-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8bd51-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8bd51-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bd51-117">HRESULT</span></span>|<span data-ttu-id="8bd51-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bd51-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bd51-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bd51-119">S_OK</span></span>|<span data-ttu-id="8bd51-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8bd51-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="8bd51-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8bd51-121">E_POINTER</span></span>|<span data-ttu-id="8bd51-122">`pwzVersion` veya `ppRuntime` null.</span><span class="sxs-lookup"><span data-stu-id="8bd51-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bd51-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bd51-123">Remarks</span></span>  
 <span data-ttu-id="8bd51-124">Bu yöntem ile eski arabirimleri gibi tutarlı bir şekilde etkileşim [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi ve eski işlevler kullanım dışı gibi `CorBindTo*` işlevleri (bkz [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API'sini barındıran .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="8bd51-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="8bd51-125">Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API için görünür olan ve yeni API ile yüklenen çalışma zamanları eski API'sine görülebilir.</span><span class="sxs-lookup"><span data-stu-id="8bd51-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd51-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bd51-126">Requirements</span></span>  
 <span data-ttu-id="8bd51-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd51-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd51-128">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8bd51-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8bd51-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8bd51-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd51-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd51-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd51-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd51-131">See also</span></span>

- [<span data-ttu-id="8bd51-132">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd51-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="8bd51-133">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="8bd51-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="8bd51-134">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8bd51-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="8bd51-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8bd51-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="8bd51-136">Barındırma</span><span class="sxs-lookup"><span data-stu-id="8bd51-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
