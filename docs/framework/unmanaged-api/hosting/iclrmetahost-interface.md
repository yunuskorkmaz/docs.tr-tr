---
description: 'Bu konuda daha fazla bilgi edinin: ICLRMetaHost arabirimi'
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
ms.openlocfilehash: 5dc50af85c067bcb525414e47cddd34070b83a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637514"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="26d06-103">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26d06-103">ICLRMetaHost Interface</span></span>

<span data-ttu-id="26d06-104">Ortak dil çalışma zamanının (CLR) sürüm numarasına göre belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, belirli bir işlemde yüklü olan tüm çalışma zamanlarını listeleme, bir derlemeyi derlemek için kullanılan CLR sürümünü bulma, temiz çalışma zamanı ile bir işlemden çıkma ve eski API bağlamasını sorgulama gibi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d06-104">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26d06-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="26d06-105">Methods</span></span>  
  
|<span data-ttu-id="26d06-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="26d06-106">Method</span></span>|<span data-ttu-id="26d06-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d06-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26d06-108">EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-108">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="26d06-109">Bir bilgisayarda yüklü her CLR sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="26d06-109">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="26d06-110">EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-110">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="26d06-111">Belirli bir işlemde yüklenen her CLR için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="26d06-111">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="26d06-112">Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md)'in yerini alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-112">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="26d06-113">ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-113">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="26d06-114">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="26d06-114">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="26d06-115">[CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-115">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="26d06-116">GetRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-116">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="26d06-117">Belirli bir CLR sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-117">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="26d06-118">Bu yöntem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-118">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="26d06-119">GetVersionFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-119">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="26d06-120">Derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), onun dosya yolu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-120">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="26d06-121">Bu yöntem, [GetFileVersion](getfileversion-function.md)'ın yerini alır.</span><span class="sxs-lookup"><span data-stu-id="26d06-121">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="26d06-122">QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-122">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="26d06-123">Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` Eski etkinleştirme API 'lerinin doğrudan kullanımı ile veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak, [ \<startup> öğe](../../configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde özniteliği kullanarak.</span><span class="sxs-lookup"><span data-stu-id="26d06-123">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="26d06-124">RequestRuntimeLoadedNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26d06-124">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="26d06-125">CLR sürümü ilk yüklendiğinde belirtilen işlev işaretçisine geri çağırma garantisi verir, ancak henüz başlatılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="26d06-125">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="26d06-126">Bu yöntem [LockClrVersion](lockclrversion-function.md) yerine geçiyor</span><span class="sxs-lookup"><span data-stu-id="26d06-126">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26d06-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26d06-127">Remarks</span></span>  

 <span data-ttu-id="26d06-128">Bu arabirimin bir örneğini almanın tek yolu, aşağıdaki gibi [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırarak olur:</span><span class="sxs-lookup"><span data-stu-id="26d06-128">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="26d06-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26d06-129">Requirements</span></span>  

 <span data-ttu-id="26d06-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d06-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d06-131">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="26d06-131">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="26d06-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="26d06-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26d06-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d06-133">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d06-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26d06-134">See also</span></span>

- [<span data-ttu-id="26d06-135">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26d06-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="26d06-136">Hosting</span><span class="sxs-lookup"><span data-stu-id="26d06-136">Hosting</span></span>](index.md)
