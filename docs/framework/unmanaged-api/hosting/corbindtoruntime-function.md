---
description: 'Daha fazla bilgi edinin: CorBindToRuntime Işlevi'
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
ms.openlocfilehash: 727abdccd692a431960d293404025cf9ccc1d7ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790093"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="59579-103">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="59579-103">CorBindToRuntime Function</span></span>

<span data-ttu-id="59579-104">Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="59579-104">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="59579-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="59579-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59579-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59579-106">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59579-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59579-107">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="59579-108">'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="59579-108">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="59579-109">.NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="59579-109">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="59579-110">Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="59579-110">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="59579-111">CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="59579-111">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="59579-112">Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="59579-112">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="59579-113">Bir ana bilgisayar, `pwszVersion`  `STARTUP_LOADER_SAFEMODE` `flags` aşağıda açıklandığı gibi, bu dolgunun ilke değerlendirmesini atlamasını ve parametresi için bir değer geçirerek belirtilen tam sürümü yüklemesini zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="59579-113">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="59579-114">Arayan için null belirtiyorsa `pwszVersion` , çalışma zamanının en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="59579-114">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="59579-115">Null geçirme, konağa çalışma zamanının hangi sürümünün yüklendiği üzerine bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="59579-115">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="59579-116">Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="59579-116">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="59579-117">'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="59579-117">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="59579-118">Geçerli değerler `svr` ve ' dir `wks` .</span><span class="sxs-lookup"><span data-stu-id="59579-118">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="59579-119">Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="59579-119">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="59579-120">`pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="59579-120">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="59579-121">Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` .</span><span class="sxs-lookup"><span data-stu-id="59579-121">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="59579-122">Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `flags` ), sunucu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="59579-122">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="59579-123">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="59579-123">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="59579-124">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="59579-124">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="59579-125">'ndaki `IID` İçindeki istenen arabirimin `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="59579-125">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="59579-126">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="59579-126">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="59579-127">dışı Döndürülen arabirim işaretçisi `riid` .</span><span class="sxs-lookup"><span data-stu-id="59579-127">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59579-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59579-128">Remarks</span></span>  

 <span data-ttu-id="59579-129">`pwszVersion`Mevcut olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="59579-129">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="59579-130">Windows kimliğinin yürütme bağlamı ve akışı</span><span class="sxs-lookup"><span data-stu-id="59579-130">Execution Context and Flow of Windows Identity</span></span>  

 <span data-ttu-id="59579-131">CLR sürüm 1 ' de, nesne, <xref:System.Security.Principal.WindowsIdentity> yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="59579-131">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="59579-132">CLR sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="59579-132">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="59579-133">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne Ayrıca herhangi bir zaman uyumsuz noktada akar.</span><span class="sxs-lookup"><span data-stu-id="59579-133">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="59579-134">Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.</span><span class="sxs-lookup"><span data-stu-id="59579-134">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="59579-135">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59579-135">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="59579-136"><xref:System.Threading.ExecutionContext>Her iş parçacığı temelinde akışı bastırmak için ayarları değiştirerek (bkz.,, <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="59579-136">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="59579-137">İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki ayarlardan bağımsız olarak nesnenin herhangi bir zaman uyumsuz noktada akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="59579-137">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="59579-138">Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="59579-138">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="59579-139">Yönetilen yürütülebilir dosyalar için, `enabled` öğesinin özniteliğini olarak ayarlamanız gerekir [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="59579-139">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="59579-140">Yönetilmeyen barındırma arabirimleri için, `STARTUP_LEGACY_IMPERSONATION` `flags` işlevini çağırırken parametresindeki bayrağı ayarlayın `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="59579-140">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="59579-141">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59579-141">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59579-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59579-142">Remarks</span></span>  

 <span data-ttu-id="59579-143">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlevi clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="59579-143">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59579-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59579-144">Requirements</span></span>  

 <span data-ttu-id="59579-145">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59579-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59579-146">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="59579-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59579-147">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59579-147">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59579-148">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59579-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59579-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59579-149">See also</span></span>

- [<span data-ttu-id="59579-150">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="59579-150">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="59579-151">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="59579-151">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="59579-152">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="59579-152">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="59579-153">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="59579-153">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="59579-154">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59579-154">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="59579-155">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="59579-155">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
