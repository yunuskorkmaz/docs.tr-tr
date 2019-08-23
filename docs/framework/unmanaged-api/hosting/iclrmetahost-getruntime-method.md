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
ms.openlocfilehash: f4b796942df153bf2c6ab703d748449331c9a0b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939855"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="a4d43-102">ICLRMetaHost::GetRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="a4d43-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="a4d43-103">Ortak dil çalışma zamanının (CLR) belirli bir sürümüne karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="a4d43-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="a4d43-104">Bu yöntem, [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a4d43-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d43-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d43-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d43-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4d43-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="a4d43-107">'ndaki Meta verilerde depolanan .NET Framework derleme sürümü, "v*A*" biçimindedir. *B* [. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="a4d43-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="a4d43-108">*A*, *B*ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="a4d43-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4d43-109">Bu parametre C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a4d43-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="a4d43-110">Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d43-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="a4d43-111">"V" ön eki gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4d43-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="a4d43-112">'ndaki İstenen arabirim için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="a4d43-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="a4d43-113">Şu anda bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4d43-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="a4d43-114">dışı İstenen çalışma zamanına karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4d43-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4d43-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4d43-115">Return Value</span></span>  
 <span data-ttu-id="a4d43-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4d43-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a4d43-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4d43-117">HRESULT</span></span>|<span data-ttu-id="a4d43-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4d43-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4d43-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4d43-119">S_OK</span></span>|<span data-ttu-id="a4d43-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a4d43-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4d43-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a4d43-121">E_POINTER</span></span>|<span data-ttu-id="a4d43-122">`pwzVersion`ya `ppRuntime` da null.</span><span class="sxs-lookup"><span data-stu-id="a4d43-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4d43-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4d43-123">Remarks</span></span>  
 <span data-ttu-id="a4d43-124">Bu yöntem [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi gibi eski arabirimlere ve kullanım dışı bırakılan `CorBindTo*` işlevler gibi eski işlevlere sürekli olarak etkileşime girer (bkz. .NET Framework 2,0 barındırma içindeki [kullanım dışı clr barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) APı).</span><span class="sxs-lookup"><span data-stu-id="a4d43-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="a4d43-125">Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API 'ye görünür ve yeni API ile yüklenen çalışma zamanları eski API 'ye görünür.</span><span class="sxs-lookup"><span data-stu-id="a4d43-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d43-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4d43-126">Requirements</span></span>  
 <span data-ttu-id="a4d43-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d43-128">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a4d43-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4d43-129">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a4d43-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4d43-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d43-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d43-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d43-131">See also</span></span>

- [<span data-ttu-id="a4d43-132">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4d43-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="a4d43-133">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="a4d43-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="a4d43-134">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a4d43-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="a4d43-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a4d43-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="a4d43-136">Barındırma</span><span class="sxs-lookup"><span data-stu-id="a4d43-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
