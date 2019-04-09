---
title: ICLRMetaHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143955"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="85438-102">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85438-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="85438-103">Kendi sürüm numarasına göre belirli bir sürümü ortak dil çalışma zamanı (CLR) döndürür, tüm yüklü CLRs listesinde, belirtilen bir işlemde yüklenen tüm çalışma zamanları listesinde, bir derlemeye derlemek, bir işleminden çıkmak için kullanılan CLR sürümü bulmak için yöntemler sağlar bir temiz çalışma zamanı kapatması ve sorgu eski API bağlama.</span><span class="sxs-lookup"><span data-stu-id="85438-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85438-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85438-104">Methods</span></span>  
  
|<span data-ttu-id="85438-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85438-105">Method</span></span>|<span data-ttu-id="85438-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85438-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85438-107">EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="85438-108">İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) bir bilgisayarda yüklü her bir CLR sürümü için arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="85438-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="85438-109">EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="85438-110">İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) yüklenen verilen bir işlemde her CLR için arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="85438-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="85438-111">Bu yöntem yerine geçer [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="85438-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="85438-112">ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="85438-113">Yüklenen tüm çalışma zamanları düzgün biçimde kapatılamadı dener ve sonra da işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="85438-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="85438-114">Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="85438-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="85438-115">GetRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="85438-116">Alır [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) belirli bir CLR sürümüne karşılık gelen arabirimi.</span><span class="sxs-lookup"><span data-stu-id="85438-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="85438-117">Bu yöntem yerine geçer [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ile kullanılan işlev [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="85438-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="85438-118">GetVersionFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="85438-119">Verilen dosya yoluna (meta verilerinde depolanır), derlemenin özgün .NET Framework derleme sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="85438-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="85438-120">Bu yöntem yerine geçer [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="85438-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="85438-121">QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="85438-122">Eski etkinleştirme İlkesi bağlı, örneğin kullanarak bir çalışma zamanı temsil eden bir arabirim döndürür `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) doğrudan kullanılarak yapılandırma dosyası girdisi eski etkinleştirme API'leri veya çağırarak [Iclrruntimeınfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85438-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="85438-123">RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85438-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="85438-124">Bir CLR sürümü ilk yüklendi, ancak henüz başlatılmadı belirtilen işlev işaretçisi için bir geri çağırma garanti eder.</span><span class="sxs-lookup"><span data-stu-id="85438-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="85438-125">Bu yöntem yerine geçer [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="85438-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85438-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85438-126">Remarks</span></span>  
 <span data-ttu-id="85438-127">Bu arabirim örneğini almak için tek çağırarak yoludur [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) gibi işlev:</span><span class="sxs-lookup"><span data-stu-id="85438-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="85438-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85438-128">Requirements</span></span>  
 <span data-ttu-id="85438-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85438-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85438-130">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="85438-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="85438-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="85438-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="85438-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="85438-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85438-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85438-133">See also</span></span>

- [<span data-ttu-id="85438-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85438-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="85438-135">Barındırma</span><span class="sxs-lookup"><span data-stu-id="85438-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
