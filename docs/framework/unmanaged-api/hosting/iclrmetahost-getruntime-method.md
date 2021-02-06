---
description: ': ICLRMetaHost:: GetRuntime yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8a2ada652dbb139337150cb8ed20986ebf8ae7f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637527"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="8d3c1-103">ICLRMetaHost::GetRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="8d3c1-103">ICLRMetaHost::GetRuntime Method</span></span>

<span data-ttu-id="8d3c1-104">Ortak dil çalışma zamanının (CLR) belirli bir sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-104">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="8d3c1-105">Bu yöntem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-105">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d3c1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d3c1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d3c1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d3c1-107">Parameters</span></span>  

 `pwzVersion`  
 <span data-ttu-id="8d3c1-108">'ndaki Meta verilerde depolanan .NET Framework derleme sürümü, "v *A*" biçimindedir. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="8d3c1-108">[in] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="8d3c1-109">*A*, *B* ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d3c1-110">Bu parametre C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-110">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="8d3c1-111">Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-111">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="8d3c1-112">"V" ön eki gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-112">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="8d3c1-113">'ndaki İstenen arabirim için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-113">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="8d3c1-114">Şu anda bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-114">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="8d3c1-115">dışı İstenen çalışma zamanına karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-115">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d3c1-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d3c1-116">Return Value</span></span>  

 <span data-ttu-id="8d3c1-117">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8d3c1-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d3c1-118">HRESULT</span></span>|<span data-ttu-id="8d3c1-119">Description</span><span class="sxs-lookup"><span data-stu-id="8d3c1-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d3c1-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d3c1-120">S_OK</span></span>|<span data-ttu-id="8d3c1-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="8d3c1-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8d3c1-122">E_POINTER</span></span>|<span data-ttu-id="8d3c1-123">`pwzVersion` ya da `ppRuntime` null.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-123">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d3c1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d3c1-124">Remarks</span></span>  

 <span data-ttu-id="8d3c1-125">Bu yöntem [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi gibi eski arabirimlere ve kullanım dışı bırakılan işlevler gibi eski işlevlere sürekli olarak etkileşime girer `CorBindTo*` (bkz. .NET Framework 2,0 barındırma API 'SINDEKI [kullanım dışı clr barındırma işlevleri](deprecated-clr-hosting-functions.md) ).</span><span class="sxs-lookup"><span data-stu-id="8d3c1-125">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="8d3c1-126">Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API 'ye görünür ve yeni API ile yüklenen çalışma zamanları eski API 'ye görünür.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-126">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d3c1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d3c1-127">Requirements</span></span>  

 <span data-ttu-id="8d3c1-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d3c1-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d3c1-129">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8d3c1-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8d3c1-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8d3c1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d3c1-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d3c1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d3c1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-132">See also</span></span>

- [<span data-ttu-id="8d3c1-133">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d3c1-133">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="8d3c1-134">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="8d3c1-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="8d3c1-135">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8d3c1-135">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="8d3c1-136">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8d3c1-136">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="8d3c1-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="8d3c1-137">Hosting</span></span>](index.md)
