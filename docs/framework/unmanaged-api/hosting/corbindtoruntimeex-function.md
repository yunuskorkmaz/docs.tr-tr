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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176506"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="e8859-102">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="e8859-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="e8859-103">Yönetilmeyen ana bilgisayarların ortak dil çalışma süresini (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8859-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="e8859-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlev CLR davranışını belirtmek için bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8859-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="e8859-105">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8859-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="e8859-106">Bu işlev, bir ana bilgisayar aşağıdakileri yapmasına izin veren bir dizi parametre alır:</span><span class="sxs-lookup"><span data-stu-id="e8859-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="e8859-107">Yüklenecek çalışma zamanının sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8859-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="e8859-108">Sunucu veya iş istasyonu yapısının yüklenip yüklenmemesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8859-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="e8859-109">Eşzamanlı çöp toplama veya eşzamanlı olmayan çöp toplama yapılıp yapılmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e8859-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8859-110">Intel Itanium mimarisini (eski adıyla IA-64) uygulayan 64 bit sistemlerde WOW64 x86 emülatörü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e8859-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="e8859-111">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için [32 bit Uygulamaları Çalıştırma'ya](/windows/desktop/WinProg64/running-32-bit-applications)bakın.</span><span class="sxs-lookup"><span data-stu-id="e8859-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="e8859-112">Derlemelerin etki alanı nötr olarak yüklenip yüklenmediğini denetle.</span><span class="sxs-lookup"><span data-stu-id="e8859-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="e8859-113">Başlatılmadan önce CLR'nin bir örneğini yapılandırmak için ek seçenekler ayarlamak için kullanılabilecek bir [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi işaretçisi edinin.</span><span class="sxs-lookup"><span data-stu-id="e8859-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8859-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8859-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8859-115">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8859-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="e8859-116">[içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="e8859-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="e8859-117">.NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="e8859-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="e8859-118">Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.</span><span class="sxs-lookup"><span data-stu-id="e8859-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="e8859-119">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e8859-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="e8859-120">Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="e8859-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="e8859-121">Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve aşağıda `STARTUP_LOADER_SAFEMODE` açıklandığı `startupFlags` gibi parametre için bir değer geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e8859-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="e8859-122">Arayan için null `pwszVersion`belirtirse, `CorBindToRuntimeEx` sürüm numaraları .NET Framework 4 çalışma zamanından daha düşük olan yüklü çalışma süreleri kümesini tanımlar ve çalışma zamanının en son sürümünü bu kümeden yükler.</span><span class="sxs-lookup"><span data-stu-id="e8859-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="e8859-123">.NET Framework 4 veya sonraki yüklenmez ve önceki sürüm yüklenmezse başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e8859-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="e8859-124">Null'u geçmek, ana bilgisayara çalışma zamanının hangi sürümünün yüklendiği üzerinde denetim vermez.</span><span class="sxs-lookup"><span data-stu-id="e8859-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="e8859-125">Bu yaklaşım bazı senaryolarda uygun olsa da, ana bilgisayara yüklemek için belirli bir sürüm sağlaması önerilir.</span><span class="sxs-lookup"><span data-stu-id="e8859-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="e8859-126">[içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e8859-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="e8859-127">Geçerli değerler `svr` `wks`ve .</span><span class="sxs-lookup"><span data-stu-id="e8859-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="e8859-128">Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.</span><span class="sxs-lookup"><span data-stu-id="e8859-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="e8859-129">Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e8859-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="e8859-130">Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile.</span><span class="sxs-lookup"><span data-stu-id="e8859-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="e8859-131">Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `startupFlags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e8859-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="e8859-132">[içinde] [numaralandırma STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="e8859-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="e8859-133">Bu bayraklar eşzamanlı çöp toplama, etki alanı nötr `pwszVersion` kodu ve parametredavranışını denetler.</span><span class="sxs-lookup"><span data-stu-id="e8859-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="e8859-134">Bayrak ayarlıdeğilse varsayılan değer tek alan adıdır.</span><span class="sxs-lookup"><span data-stu-id="e8859-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="e8859-135">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e8859-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="e8859-136">Bu bayrakların açıklamaları için [numaralandırmanın STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="e8859-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="e8859-137">[içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass.</span><span class="sxs-lookup"><span data-stu-id="e8859-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="e8859-138">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e8859-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="e8859-139">[içinde] İstenen `IID` arabirimin `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="e8859-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="e8859-140">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e8859-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e8859-141">[çıkış] Döndürülen arabirim `riid`işaretçisi .</span><span class="sxs-lookup"><span data-stu-id="e8859-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8859-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8859-142">Remarks</span></span>  
 <span data-ttu-id="e8859-143">Var `pwszVersion` olmayan bir çalışma zamanı sürümü belirtirse, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD Bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8859-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="e8859-144">Yürütme Bağlamı ve Windows Kimliğinin Akışı</span><span class="sxs-lookup"><span data-stu-id="e8859-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="e8859-145">CLR'nin sürüm <xref:System.Security.Principal.WindowsIdentity> 1'inde, nesne yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri aramaları gibi eşzamanlı noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="e8859-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="e8859-146">CLR'nin sürüm 2.0'ında, bir <xref:System.Threading.ExecutionContext> nesne şu anda çalıştırılamakta olan iş parçacığı yla ilgili bazı bilgileri sarar ve uygulama etki alanı sınırları boyunca değil, herhangi bir eşzamanlı nokta boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="e8859-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="e8859-147">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir asynchronous noktası boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="e8859-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="e8859-148">Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme, varsa, çok akar.</span><span class="sxs-lookup"><span data-stu-id="e8859-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="e8859-149">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8859-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="e8859-150">İş parçacığı <xref:System.Threading.ExecutionContext> başına akışı bastırmak için ayarları değiştirerek (bkz. <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="e8859-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="e8859-151">İşlem varsayılan modunu, geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> ayarlardan bağımsız olarak nesnenin herhangi bir eşyoknom noktası boyunca akmayan sürüm 1 uyumluluk moduna değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="e8859-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="e8859-152">Varsayılan modu nasıl değiştirdiğiniz, CLR'yi yüklemek için yönetilen bir yürütülebilir veya yönetilmeyen bir barındırma arabirimi kullanıp kullanmadığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="e8859-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="e8859-153">Yönetilen yürütülebilir ler için `enabled` [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="e8859-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="e8859-154">Yönetilmeyen barındırma arabirimleri `STARTUP_LEGACY_IMPERSONATION` `startupFlags` `CorBindToRuntimeEx` için, işlevi ararken parametredeki bayrağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8859-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="e8859-155">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e8859-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8859-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8859-156">Requirements</span></span>  
 <span data-ttu-id="e8859-157">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8859-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8859-158">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8859-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8859-159">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e8859-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8859-160">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8859-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8859-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8859-161">See also</span></span>

- [<span data-ttu-id="e8859-162">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="e8859-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="e8859-163">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="e8859-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="e8859-164">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="e8859-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="e8859-165">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="e8859-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="e8859-166">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8859-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="e8859-167">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e8859-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
