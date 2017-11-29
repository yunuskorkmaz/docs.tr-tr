---
title: "CorBindToRuntime İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a833be39f93082e8d2c0cb28f435f754143721f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="a98a7-102">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="a98a7-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="a98a7-103">Ortak dil çalışma zamanı (CLR) süreç içine yüklemek için yönetilmeyen konakları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="a98a7-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a98a7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a98a7-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a98a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a98a7-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="a98a7-107">[in] Yüklemek istediğiniz CLR sürümü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="a98a7-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="a98a7-108">.NET Framework sürüm numarası noktalarla ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="a98a7-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="a98a7-109">Dize olarak geçirilen `pwszVersion` sürüm numarası (örneğin, "v1.0.1529") ilk üç bölümleri tarafından izlenen "v" karakter ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a98a7-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="a98a7-110">CLR bazı sürümleri CLR önceki sürümleriyle uyumluluk belirten bir ilke bildirimi ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="a98a7-111">Varsayılan olarak, başlatma dolgusu değerlendirir `pwszVersion` ilke deyimleri ve yükleri karşı çalışma zamanı en son sürümü olan istenen sürümü ile uyumlu.</span><span class="sxs-lookup"><span data-stu-id="a98a7-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="a98a7-112">Bir ana bilgisayar ilkesi değerlendirmesi atlayın ve belirtilen tam sürümünü yüklemek için dolgu zorlayabilirsiniz `pwszVersion` değerini geçirerek `STARTUP_LOADER_SAFEMODE` için `flags` aşağıda açıklandığı gibi parametre.</span><span class="sxs-lookup"><span data-stu-id="a98a7-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="a98a7-113">Arayan için null belirtiyorsa `pwszVersion`, çalışma zamanı en son sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="a98a7-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="a98a7-114">Null geçirme konak çalışma zamanı sürümü yüklendiği hiçbir denetim olanağı verir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="a98a7-115">Bu yaklaşım bazı senaryolarda uygun olmakla birlikte, konak yüklemek için belirli bir sürümü sağlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="a98a7-116">[in] Sunucu veya CLR iş istasyonu yapı yük belirtir bir dize.</span><span class="sxs-lookup"><span data-stu-id="a98a7-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="a98a7-117">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="a98a7-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="a98a7-118">Server yapı çöp koleksiyonları için birden çok işlemci yararlanmak için optimize edilmiştir ve iş istasyonu yapı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="a98a7-119">Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derleme yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="a98a7-120">Bir tek işlemcili makine üzerinde çalışan iş istasyonu derleme her zaman yüklenir, olsa bile `pwszBuildFlavor` ayarlanır `svr`.</span><span class="sxs-lookup"><span data-stu-id="a98a7-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="a98a7-121">Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı atık toplama belirtilir (açıklamasına bakın `flags` parametresi), sunucu derleme yüklendi.</span><span class="sxs-lookup"><span data-stu-id="a98a7-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a98a7-122">[in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a98a7-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a98a7-123">Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a98a7-124">[in] `IID` İstenen arabiriminden, `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="a98a7-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="a98a7-125">Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a98a7-126">[out] Döndürülen arabirimi işaretçisi `riid`.</span><span class="sxs-lookup"><span data-stu-id="a98a7-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98a7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a98a7-127">Remarks</span></span>  
 <span data-ttu-id="a98a7-128">Varsa `pwszVersion` yok, bir çalışma zamanı sürümü belirtir `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a98a7-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="a98a7-129">Yürütme bağlamı ve Windows Identity akışı</span><span class="sxs-lookup"><span data-stu-id="a98a7-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="a98a7-130">CLR 1 sürümünde <xref:System.Security.Principal.WindowsIdentity> nesne yeni iş parçacığı, iş parçacığı havuzları ya da Zamanlayıcı geri aramalar gibi zaman uyumsuz noktaları arasında akış değil.</span><span class="sxs-lookup"><span data-stu-id="a98a7-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="a98a7-131">CLR 2.0 sürümünde bir <xref:System.Threading.ExecutionContext> nesne şu anda yürütülen iş parçacığı hakkında bazı bilgiler sarmalar ve herhangi bir zaman uyumsuz noktası arasında ancak uygulama etki alanı sınırları boyunca değil akar.</span><span class="sxs-lookup"><span data-stu-id="a98a7-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="a98a7-132">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de hiçbir zaman uyumsuz noktası üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="a98a7-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="a98a7-133">Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme varsa, çok akar.</span><span class="sxs-lookup"><span data-stu-id="a98a7-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="a98a7-134">İki yolla akış değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a98a7-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="a98a7-135">Değiştirerek <xref:System.Threading.ExecutionContext> akışını bir iş parçacığı başına temelinde gizlemek için ayarları (bkz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="a98a7-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="a98a7-136">Sürüm 1 uyumluluk moduna işlemi varsayılan modu değiştirerek nerede <xref:System.Security.Principal.WindowsIdentity> nesne akan tüm zaman uyumsuz noktası üzerinden bağımsız olarak, <xref:System.Threading.ExecutionContext> geçerli iş parçacığının ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a98a7-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="a98a7-137">Varsayılan modunu değiştirmek nasıl olup, yönetilen bir yürütülebilir dosya veya yönetilmeyen bir barındırma arabirimi CLR yüklemeye kullanmasına bağlı olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="a98a7-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="a98a7-138">Yönetilen yürütülebilir dosyalar için ayarlamanız gerekir `enabled` özniteliği [ \<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="a98a7-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="a98a7-139">Barındırma arabirimleri yönetilmeyen ayarlamanız `STARTUP_LEGACY_IMPERSONATION` içinde bayrak `flags` çağırırken parametre `CorBindToRuntimeEx` işlevi.</span><span class="sxs-lookup"><span data-stu-id="a98a7-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="a98a7-140">Sürüm 1 uyumluluk modu, tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a98a7-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98a7-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a98a7-141">Remarks</span></span>  
 <span data-ttu-id="a98a7-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirmek ancak `CorBindToRuntimeEx` işlevi CLR davranışını belirtmek için bayrakları ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a98a7-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a98a7-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a98a7-143">Requirements</span></span>  
 <span data-ttu-id="a98a7-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a98a7-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a98a7-145">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a98a7-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a98a7-146">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a98a7-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a98a7-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a98a7-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98a7-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a98a7-148">See Also</span></span>  
 [<span data-ttu-id="a98a7-149">CorBindToCurrentRuntime işlevi</span><span class="sxs-lookup"><span data-stu-id="a98a7-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="a98a7-150">CorBindToRuntimeByCfg işlevi</span><span class="sxs-lookup"><span data-stu-id="a98a7-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="a98a7-151">CorBindToRuntimeEx işlevi</span><span class="sxs-lookup"><span data-stu-id="a98a7-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="a98a7-152">CorBindToRuntimeHost işlevi</span><span class="sxs-lookup"><span data-stu-id="a98a7-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="a98a7-153">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="a98a7-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="a98a7-154">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="a98a7-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
