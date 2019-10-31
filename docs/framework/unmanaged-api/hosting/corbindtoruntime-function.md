---
title: CorBindToRuntime İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138303"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="3b906-102">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3b906-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="3b906-103">Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b906-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="3b906-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3b906-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b906-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b906-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b906-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b906-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="3b906-107">'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="3b906-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="3b906-108">.NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="3b906-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="3b906-109">`pwszVersion` olarak geçirilen dize "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="3b906-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="3b906-110">CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3b906-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="3b906-111">Varsayılan olarak, başlangıç dolgusu ilke deyimlerine karşı `pwszVersion` değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="3b906-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="3b906-112">Bir ana bilgisayar, aşağıda açıklandığı gibi `flags` parametresi için bir `STARTUP_LOADER_SAFEMODE` değeri geçirerek, dolgunun ilke değerlendirmesini atlayıp `pwszVersion` belirtilen tam sürümü yüklemesine zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3b906-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="3b906-113">Arayan `pwszVersion`için null belirtiyorsa, çalışma zamanının en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3b906-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="3b906-114">Null geçirme, konağa çalışma zamanının hangi sürümünün yüklendiği üzerine bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b906-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="3b906-115">Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="3b906-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="3b906-116">'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3b906-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="3b906-117">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="3b906-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="3b906-118">Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3b906-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="3b906-119">`pwszBuildFlavor` null olarak ayarlandıysa, iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3b906-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="3b906-120">Tek işlemcili bir makinede çalışırken, `pwszBuildFlavor` `svr`olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3b906-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="3b906-121">Ancak, `pwszBuildFlavor` `svr` olarak ayarlanırsa ve eşzamanlı çöp toplama belirtilirse (`flags` parametresinin açıklamasına bakın), sunucu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3b906-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3b906-122">'ndaki [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass 'ın `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="3b906-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3b906-123">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="3b906-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3b906-124">'ndaki İstenen arabirimin `rclsid``IID`.</span><span class="sxs-lookup"><span data-stu-id="3b906-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="3b906-125">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="3b906-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3b906-126">dışı `riid`için döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3b906-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b906-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b906-127">Remarks</span></span>  
 <span data-ttu-id="3b906-128">`pwszVersion` var olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b906-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="3b906-129">Windows kimliğinin yürütme bağlamı ve akışı</span><span class="sxs-lookup"><span data-stu-id="3b906-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="3b906-130">CLR sürüm 1 ' de, <xref:System.Security.Principal.WindowsIdentity> nesnesi yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalara akmaz.</span><span class="sxs-lookup"><span data-stu-id="3b906-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="3b906-131">CLR sürüm 2,0 ' de, bir <xref:System.Threading.ExecutionContext> nesnesi şu anda yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="3b906-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="3b906-132">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesnesi de herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="3b906-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="3b906-133">Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.</span><span class="sxs-lookup"><span data-stu-id="3b906-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="3b906-134">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b906-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="3b906-135">İş parçacığı temelinde akışı bastırmak için <xref:System.Threading.ExecutionContext> ayarlarını değiştirerek (<xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemlerine bakın).</span><span class="sxs-lookup"><span data-stu-id="3b906-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="3b906-136">İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> nesnenin geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> ayarlarından bağımsız olarak herhangi bir zaman uyumsuz noktada akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="3b906-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="3b906-137">Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="3b906-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="3b906-138">Yönetilen yürütülebilir dosyalar için [\<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin `enabled` özniteliğini `true`olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b906-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="3b906-139">Yönetilmeyen barındırma arabirimleri için, `CorBindToRuntimeEx` işlevini çağırırken `flags` parametresindeki `STARTUP_LEGACY_IMPERSONATION` bayrağını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3b906-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="3b906-140">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3b906-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b906-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b906-141">Remarks</span></span>  
 <span data-ttu-id="3b906-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` IşLEVI, clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b906-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b906-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b906-143">Requirements</span></span>  
 <span data-ttu-id="3b906-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b906-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b906-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b906-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b906-146">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b906-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b906-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b906-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b906-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b906-148">See also</span></span>

- [<span data-ttu-id="3b906-149">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3b906-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3b906-150">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="3b906-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="3b906-151">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="3b906-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="3b906-152">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="3b906-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="3b906-153">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b906-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="3b906-154">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3b906-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
