---
title: CorBindToRuntimeEx İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03972ac38a5259443f43a4f91002bf8dc717509f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466303"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="0f49a-102">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f49a-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="0f49a-103">Ortak dil çalışma zamanı (CLR) bir işleme yüklemek için yöneilmeyen ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="0f49a-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri gerçekleştiren aynı işlemi ancak `CorBindToRuntimeEx` işlevi CLR'nin davranışını belirtmek için bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f49a-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="0f49a-105">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f49a-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="0f49a-106">Bu işlev konak aşağıdakileri yapmasına izin vermek parametreleri kümesini alır:</span><span class="sxs-lookup"><span data-stu-id="0f49a-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="0f49a-107">Yüklenecek çalışma zamanı sürümü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0f49a-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="0f49a-108">Sunucu veya iş istasyonunun derleme yüklü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="0f49a-109">Eş zamanlı çöp toplama veya eşzamansız atık toplama yapılan olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="0f49a-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f49a-110">Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü.</span><span class="sxs-lookup"><span data-stu-id="0f49a-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="0f49a-111">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="0f49a-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
-   <span data-ttu-id="0f49a-112">Etki alanından bağımsız yüklenen derlemeleri olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="0f49a-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="0f49a-113">Bir arabirim işaretçisi elde bir [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) başlamadan önce CLR örneği yapılandırmak için ek seçenekleri ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f49a-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f49a-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f49a-115">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f49a-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="0f49a-116">[in] Yüklemek istediğiniz CLR sürümünü tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="0f49a-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0f49a-117">.NET Framework uygulamasındaki sürüm numarası noktayla ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="0f49a-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0f49a-118">Olarak geçen dize `pwszVersion` (örneğin, "v1.0.1529") sürüm numarasının ilk üç parçalar tarafından izlenen "v" karakteriyle başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f49a-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0f49a-119">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0f49a-120">Varsayılan olarak, başlangıç dolgusu değerlendirir `pwszVersion` ilke bildirimlerine ve yükleri karşı çalışma zamanının en son sürümü olan istenen sürümle uyumlu.</span><span class="sxs-lookup"><span data-stu-id="0f49a-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0f49a-121">Bir konak ilke değerlendirmesini atlamaya ve belirtilen tam sürümü yüklemeye zorlayabilir `pwszVersion` değerini geçirerek `STARTUP_LOADER_SAFEMODE` için `startupFlags` aşağıda açıklandığı gibi parametre.</span><span class="sxs-lookup"><span data-stu-id="0f49a-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="0f49a-122">Arayan için null belirtiyorsa `pwszVersion`, `CorBindToRuntimeEx` yüklü olan sürüm numaraları, .NET Framework 4 çalışma zamanı düşüktür ve bu kümeden çalışma zamanının en son sürümünü yükler çalışma zamanları kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f49a-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="0f49a-123">Önceki bir sürümü yüklü değilse .NET Framework 4 veya sonrasını ve başarısız yüklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0f49a-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="0f49a-124">Null geçirme konak çalışma zamanının yüklendiği üzerinde hiçbir denetimi verdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f49a-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="0f49a-125">Bu yaklaşım bazı senaryolarda uygun olsa da, konağın belirli bir sürümünü yüklemek için sağlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0f49a-126">[in] Sunucunun veya CLR çalışma istasyonu yapısı yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0f49a-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0f49a-127">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="0f49a-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0f49a-128">Sunucu yapısı çöp toplama için birden çok işlemciden yararlanmak için optimize edilmiştir ve çalışma istasyonu yapısı tek işlemcili makinede çalışan istemci uygulamaları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0f49a-129">Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0f49a-130">İş istasyonu yapısı, bir tek işlemcili makinede çalışırken daima yüklenir, bile `pwszBuildFlavor` ayarlanır `svr`.</span><span class="sxs-lookup"><span data-stu-id="0f49a-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0f49a-131">Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eş zamanlı çöp toplama belirtilmişse (açıklamasına bakın `startupFlags` parametresi), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="0f49a-132">[in] Değerlerinin bir birleşimini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0f49a-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="0f49a-133">Bu bayraklar eş zamanlı çöp toplama, alan-bağımsız kod ve davranışını denetleyen `pwszVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0f49a-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="0f49a-134">Varsayılan, hiçbir bayrak ayarlanmışsa tek etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="0f49a-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="0f49a-135">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0f49a-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="0f49a-136">Bu bayraklar açıklamaları için bkz. [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0f49a-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0f49a-137">[in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0f49a-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0f49a-138">Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="0f49a-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0f49a-139">[in] `IID` , İstenen arabiriminden `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="0f49a-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="0f49a-140">Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="0f49a-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0f49a-141">[out] Döndürülen arabirim işaretçisi `riid`.</span><span class="sxs-lookup"><span data-stu-id="0f49a-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f49a-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f49a-142">Remarks</span></span>  
 <span data-ttu-id="0f49a-143">Varsa `pwszVersion` mevcut değil, bir çalışma zamanı sürümünü belirten `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD bir HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f49a-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="0f49a-144">Yürütme bağlamı ve Windows Identity akışı</span><span class="sxs-lookup"><span data-stu-id="0f49a-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="0f49a-145">CLR sürüm 1 <xref:System.Security.Principal.WindowsIdentity> nesne yeni iş parçacığı, iş parçacığı havuzları ya da Zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalar arasında akış değil.</span><span class="sxs-lookup"><span data-stu-id="0f49a-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="0f49a-146">CLR 2.0 sürümünde bir <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığını hakkında bazı bilgiler sarmalar ve herhangi bir zaman uyumsuz noktası arasında ancak olmayan uygulama etki alanı sınırları üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="0f49a-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="0f49a-147">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir zaman uyumsuz noktası üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="0f49a-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="0f49a-148">Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme varsa, çok akar.</span><span class="sxs-lookup"><span data-stu-id="0f49a-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="0f49a-149">Flow'a iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f49a-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="0f49a-150">Değiştirerek <xref:System.Threading.ExecutionContext> akışını bir iş parçacığı başına temelinde bastırmak için ayarları (bkz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="0f49a-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="0f49a-151">Sürüm 1 uyumluluk modu için varsayılan işlem modu değiştirerek burada <xref:System.Security.Principal.WindowsIdentity> nesne akan tüm zaman uyumsuz noktası üzerinden açmamasından <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0f49a-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="0f49a-152">Varsayılan mod nasıl değiştirmeniz mi yönetilen bir yürütülebilir dosya veya yönetilmeyen bir barındırma arabiriminin CLR'yi yüklemek için kullandığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="0f49a-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="0f49a-153">Yönetilen yürütülebilir dosyalar için ayarlamanız gerekir `enabled` özniteliği [ \<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="0f49a-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="0f49a-154">Yönetilmeyen barındırma arabirimleri için ayarlanan `STARTUP_LEGACY_IMPERSONATION` bayrağını `startupFlags` çağırırken parametre `CorBindToRuntimeEx` işlevi.</span><span class="sxs-lookup"><span data-stu-id="0f49a-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="0f49a-155">Sürüm 1 uyumluluk modu, tüm işlem ve işlemde tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0f49a-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f49a-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f49a-156">Requirements</span></span>  
 <span data-ttu-id="0f49a-157">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f49a-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f49a-158">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f49a-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f49a-159">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f49a-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f49a-160">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f49a-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f49a-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f49a-161">See also</span></span>
- [<span data-ttu-id="0f49a-162">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f49a-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0f49a-163">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f49a-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="0f49a-164">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f49a-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0f49a-165">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f49a-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="0f49a-166">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f49a-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="0f49a-167">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0f49a-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
