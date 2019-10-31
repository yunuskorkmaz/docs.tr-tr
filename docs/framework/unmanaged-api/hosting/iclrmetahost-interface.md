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
ms.openlocfilehash: bb760f4923cc3530a28bc68180db743ee468b51d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140903"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="4143d-102">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4143d-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="4143d-103">Ortak dil çalışma zamanının (CLR) sürüm numarasına göre belirli bir sürümünü döndüren yöntemler sağlar, tüm yüklü CLRs 'leri listeleme, belirli bir işlemde yüklü olan tüm çalışma zamanlarını listeleme, bir derlemeyi derlemek için kullanılan CLR sürümünü bulma, bir işlemden çıkma temiz bir çalışma zamanı kapatması ve eski API bağlamasını sorgula.</span><span class="sxs-lookup"><span data-stu-id="4143d-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4143d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4143d-104">Methods</span></span>  
  
|<span data-ttu-id="4143d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4143d-105">Method</span></span>|<span data-ttu-id="4143d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4143d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4143d-107">EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="4143d-108">Bir bilgisayarda yüklü her CLR sürümü için geçerli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4143d-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="4143d-109">EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="4143d-110">Belirli bir işlemde yüklenen her CLR için geçerli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4143d-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="4143d-111">Bu yöntem [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)'in yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="4143d-112">ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="4143d-113">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4143d-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="4143d-114">[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="4143d-115">GetRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="4143d-116">Belirli bir CLR sürümüne karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="4143d-117">Bu yöntem, [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="4143d-118">GetVersionFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="4143d-119">Derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), onun dosya yolu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="4143d-120">Bu yöntem, [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)'ın yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4143d-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="4143d-121">QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="4143d-122">Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, [\<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde `useLegacyV2RuntimeActivationPolicy` özniteliği kullanarak, eski etkinleştirme API 'lerinin doğrudan kullanımı veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="4143d-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="4143d-123">RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4143d-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="4143d-124">CLR sürümü ilk yüklendiğinde belirtilen işlev işaretçisine geri çağırma garantisi verir, ancak henüz başlatılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4143d-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="4143d-125">Bu yöntem [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) yerine geçiyor</span><span class="sxs-lookup"><span data-stu-id="4143d-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4143d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4143d-126">Remarks</span></span>  
 <span data-ttu-id="4143d-127">Bu arabirimin bir örneğini almanın tek yolu, aşağıdaki gibi [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini çağırarak olur:</span><span class="sxs-lookup"><span data-stu-id="4143d-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4143d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4143d-128">Requirements</span></span>  
 <span data-ttu-id="4143d-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4143d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4143d-130">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4143d-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4143d-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4143d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4143d-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4143d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4143d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4143d-133">See also</span></span>

- [<span data-ttu-id="4143d-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4143d-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4143d-135">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4143d-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
