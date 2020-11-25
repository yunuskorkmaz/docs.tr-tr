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
ms.openlocfilehash: 75c8d550e572795a291f4639f9f28bd5214ff188
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714022"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="704f4-102">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="704f4-102">ICLRMetaHost Interface</span></span>

<span data-ttu-id="704f4-103">Ortak dil çalışma zamanının (CLR) sürüm numarasına göre belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, belirli bir işlemde yüklü olan tüm çalışma zamanlarını listeleme, bir derlemeyi derlemek için kullanılan CLR sürümünü bulma, temiz çalışma zamanı ile bir işlemden çıkma ve eski API bağlamasını sorgulama gibi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="704f4-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="704f4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="704f4-104">Methods</span></span>  
  
|<span data-ttu-id="704f4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="704f4-105">Method</span></span>|<span data-ttu-id="704f4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="704f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="704f4-107">EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-107">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="704f4-108">Bir bilgisayarda yüklü her CLR sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="704f4-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="704f4-109">EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-109">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="704f4-110">Belirli bir işlemde yüklenen her CLR için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="704f4-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="704f4-111">Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md)'in yerini alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="704f4-112">ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-112">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="704f4-113">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="704f4-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="704f4-114">[CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="704f4-115">GetRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-115">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="704f4-116">Belirli bir CLR sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-116">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="704f4-117">Bu yöntem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-117">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="704f4-118">GetVersionFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-118">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="704f4-119">Derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), onun dosya yolu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="704f4-120">Bu yöntem, [GetFileVersion](getfileversion-function.md)'ın yerini alır.</span><span class="sxs-lookup"><span data-stu-id="704f4-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="704f4-121">QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-121">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="704f4-122">Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` Eski etkinleştirme API 'lerinin doğrudan kullanımı ile veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak, [ \<startup> öğe](../../configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde özniteliği kullanarak.</span><span class="sxs-lookup"><span data-stu-id="704f4-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="704f4-123">RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="704f4-123">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="704f4-124">CLR sürümü ilk yüklendiğinde belirtilen işlev işaretçisine geri çağırma garantisi verir, ancak henüz başlatılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="704f4-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="704f4-125">Bu yöntem [LockClrVersion](lockclrversion-function.md) yerine geçiyor</span><span class="sxs-lookup"><span data-stu-id="704f4-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="704f4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="704f4-126">Remarks</span></span>  

 <span data-ttu-id="704f4-127">Bu arabirimin bir örneğini almanın tek yolu, aşağıdaki gibi [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırarak olur:</span><span class="sxs-lookup"><span data-stu-id="704f4-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="704f4-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="704f4-128">Requirements</span></span>  

 <span data-ttu-id="704f4-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="704f4-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="704f4-130">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="704f4-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="704f4-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="704f4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="704f4-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="704f4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704f4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="704f4-133">See also</span></span>

- [<span data-ttu-id="704f4-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="704f4-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="704f4-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="704f4-135">Hosting</span></span>](index.md)
