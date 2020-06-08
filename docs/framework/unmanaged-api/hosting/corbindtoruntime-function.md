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
ms.openlocfilehash: 52594c36c54c74941371f9950fbc6fb543b86de0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493558"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="920fd-102">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="920fd-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="920fd-103">Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="920fd-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="920fd-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="920fd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920fd-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="920fd-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="920fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="920fd-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="920fd-107">'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="920fd-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="920fd-108">.NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="920fd-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="920fd-109">Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="920fd-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="920fd-110">CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="920fd-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="920fd-111">Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="920fd-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="920fd-112">Bir ana bilgisayar, `pwszVersion` `STARTUP_LOADER_SAFEMODE` `flags` aşağıda açıklandığı gibi, bu dolgunun ilke değerlendirmesini atlamasını ve parametresi için bir değer geçirerek belirtilen tam sürümü yüklemesini zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="920fd-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="920fd-113">Arayan için null belirtiyorsa `pwszVersion` , çalışma zamanının en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="920fd-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="920fd-114">Null geçirme, konağa çalışma zamanının hangi sürümünün yüklendiği üzerine bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="920fd-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="920fd-115">Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="920fd-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="920fd-116">'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="920fd-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="920fd-117">Geçerli değerler `svr` ve ' dir `wks` .</span><span class="sxs-lookup"><span data-stu-id="920fd-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="920fd-118">Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="920fd-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="920fd-119">`pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="920fd-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="920fd-120">Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` .</span><span class="sxs-lookup"><span data-stu-id="920fd-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="920fd-121">Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `flags` ), sunucu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="920fd-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="920fd-122">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="920fd-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="920fd-123">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="920fd-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="920fd-124">'ndaki `IID`İçindeki istenen arabirimin `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="920fd-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="920fd-125">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="920fd-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="920fd-126">dışı Döndürülen arabirim işaretçisi `riid` .</span><span class="sxs-lookup"><span data-stu-id="920fd-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="920fd-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="920fd-127">Remarks</span></span>  
 <span data-ttu-id="920fd-128">`pwszVersion`Mevcut olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="920fd-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="920fd-129">Windows kimliğinin yürütme bağlamı ve akışı</span><span class="sxs-lookup"><span data-stu-id="920fd-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="920fd-130">CLR sürüm 1 ' de, nesne, <xref:System.Security.Principal.WindowsIdentity> yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="920fd-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="920fd-131">CLR sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="920fd-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="920fd-132">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne Ayrıca herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="920fd-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="920fd-133">Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.</span><span class="sxs-lookup"><span data-stu-id="920fd-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="920fd-134">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="920fd-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="920fd-135"><xref:System.Threading.ExecutionContext>Her iş parçacığı temelinde akışı bastırmak için ayarları değiştirerek (bkz.,, <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="920fd-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="920fd-136">İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki ayarlardan bağımsız olarak nesnenin herhangi bir zaman uyumsuz noktada akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="920fd-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="920fd-137">Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="920fd-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="920fd-138">Yönetilen yürütülebilir dosyalar için, `enabled` öğesinin özniteliğini olarak ayarlamanız gerekir [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="920fd-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="920fd-139">Yönetilmeyen barındırma arabirimleri için, `STARTUP_LEGACY_IMPERSONATION` `flags` işlevini çağırırken parametresindeki bayrağı ayarlayın `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="920fd-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="920fd-140">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="920fd-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="920fd-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="920fd-141">Remarks</span></span>  
 <span data-ttu-id="920fd-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlevi clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="920fd-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="920fd-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="920fd-143">Requirements</span></span>  
 <span data-ttu-id="920fd-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="920fd-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="920fd-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="920fd-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="920fd-146">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="920fd-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="920fd-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="920fd-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920fd-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="920fd-148">See also</span></span>

- [<span data-ttu-id="920fd-149">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="920fd-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="920fd-150">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="920fd-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="920fd-151">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="920fd-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="920fd-152">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="920fd-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="920fd-153">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="920fd-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="920fd-154">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="920fd-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
