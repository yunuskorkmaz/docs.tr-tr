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
ms.openlocfilehash: dcf2ce8bdb7cec1f567e548ff3314e160fffe9fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616638"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="6afa4-102">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="6afa4-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="6afa4-103">Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6afa4-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="6afa4-104">[CorBindToRuntime](corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlevi clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6afa4-104">The [CorBindToRuntime](corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="6afa4-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6afa4-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="6afa4-106">Bu işlev, bir ana bilgisayarın aşağıdakileri yapmasına izin veren bir parametre kümesi alır:</span><span class="sxs-lookup"><span data-stu-id="6afa4-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="6afa4-107">Yüklenecek çalışma zamanının sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="6afa4-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="6afa4-108">Sunucu veya iş istasyonu derlemesinin yüklenip yüklenmeyeceğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6afa4-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="6afa4-109">Eşzamanlı atık toplama veya eşzamanlı olmayan çöp toplamanın gerçekleştirilip yapılmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6afa4-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6afa4-110">Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6afa4-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="6afa4-111">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="6afa4-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="6afa4-112">Derlemelerin etki alanı nötr olarak yüklenip yüklenmediğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6afa4-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="6afa4-113">Bir [ICorRuntimeHost](icorruntimehost-interface.md) için, başlamadan önce clr örneğini yapılandırmak için ek seçenekler ayarlamak üzere kullanılabilecek bir arabirim işaretçisi edinin.</span><span class="sxs-lookup"><span data-stu-id="6afa4-113">Obtain an interface pointer to an [ICorRuntimeHost](icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afa4-114">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6afa4-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6afa4-115">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6afa4-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="6afa4-116">'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="6afa4-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="6afa4-117">.NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="6afa4-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="6afa4-118">Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="6afa4-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="6afa4-119">CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="6afa4-120">Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="6afa4-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="6afa4-121">Bir ana bilgisayar, `pwszVersion` `STARTUP_LOADER_SAFEMODE` `startupFlags` aşağıda açıklandığı gibi, bu dolgunun ilke değerlendirmesini atlamasını ve parametresi için bir değer geçirerek belirtilen tam sürümü yüklemesini zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="6afa4-122">Çağıran için null belirtiyorsa `pwszVersion` , `CorBindToRuntimeEx` sürüm numaraları .NET Framework 4 çalışma zamanından daha düşük olan yüklü çalışma zamanları kümesini tanımlar ve bu kümeden çalışma zamanının en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="6afa4-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="6afa4-123">.NET Framework 4 veya sonraki bir sürümü yüklemez ve eski sürüm yüklenmemişse başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6afa4-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="6afa4-124">Null geçirildiğine, ana bilgisayarın hangi çalışma zamanının sürümünün yüklü olmadığını belirten bir denetim verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="6afa4-125">Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="6afa4-126">'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6afa4-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="6afa4-127">Geçerli değerler `svr` ve ' dir `wks` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="6afa4-128">Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="6afa4-129">`pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="6afa4-130">Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="6afa4-131">Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `startupFlags` ), sunucu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="6afa4-132">'ndaki [Startup_flags](startup-flags-enumeration.md) numaralandırması değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6afa4-132">[in] A combination of values of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="6afa4-133">Bu bayraklar, eşzamanlı atık toplamayı, etki alanını bağımsız kodu ve parametresinin davranışını denetler `pwszVersion` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="6afa4-134">Hiçbir bayrak ayarlanmamışsa varsayılan, tek etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="6afa4-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="6afa4-135">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="6afa4-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="6afa4-136">Bu bayrakların açıklamaları için [startup_flags](startup-flags-enumeration.md) sabit listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="6afa4-136">For descriptions of these flags, see the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="6afa4-137">'ndaki `CLSID` [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="6afa4-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="6afa4-138">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6afa4-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="6afa4-139">'ndaki `IID`İçindeki istenen arabirimin `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="6afa4-140">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6afa4-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="6afa4-141">dışı Döndürülen arabirim işaretçisi `riid` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6afa4-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6afa4-142">Remarks</span></span>  
 <span data-ttu-id="6afa4-143">`pwszVersion`Mevcut olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6afa4-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="6afa4-144">Windows kimliğinin yürütme bağlamı ve akışı</span><span class="sxs-lookup"><span data-stu-id="6afa4-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="6afa4-145">CLR sürüm 1 ' de, nesne, <xref:System.Security.Principal.WindowsIdentity> yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6afa4-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="6afa4-146">CLR sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="6afa4-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="6afa4-147">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne Ayrıca herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="6afa4-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="6afa4-148">Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.</span><span class="sxs-lookup"><span data-stu-id="6afa4-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="6afa4-149">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6afa4-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="6afa4-150"><xref:System.Threading.ExecutionContext>Her iş parçacığı temelinde akışı bastırmak için ayarları değiştirerek (bkz.,, <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="6afa4-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="6afa4-151">İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki ayarlardan bağımsız olarak nesnenin herhangi bir zaman uyumsuz noktada akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6afa4-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="6afa4-152">Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="6afa4-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="6afa4-153">Yönetilen yürütülebilir dosyalar için, `enabled` [ \< legacyımpersonationpolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin özniteliğini olarak ayarlamanız gerekir `true` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="6afa4-154">Yönetilmeyen barındırma arabirimleri için, `STARTUP_LEGACY_IMPERSONATION` `startupFlags` işlevini çağırırken parametresindeki bayrağı ayarlayın `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="6afa4-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="6afa4-155">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6afa4-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6afa4-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6afa4-156">Requirements</span></span>  
 <span data-ttu-id="6afa4-157">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afa4-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afa4-158">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6afa4-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6afa4-159">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6afa4-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6afa4-160">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afa4-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afa4-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6afa4-161">See also</span></span>

- [<span data-ttu-id="6afa4-162">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="6afa4-162">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="6afa4-163">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="6afa4-163">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="6afa4-164">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="6afa4-164">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="6afa4-165">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="6afa4-165">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="6afa4-166">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6afa4-166">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="6afa4-167">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6afa4-167">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
