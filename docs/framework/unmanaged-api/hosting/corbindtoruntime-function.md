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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176519"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="008a2-102">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="008a2-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="008a2-103">Yönetilmeyen ana bilgisayarların ortak dil çalışma süresini (CLR) bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="008a2-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="008a2-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="008a2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="008a2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="008a2-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="008a2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="008a2-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="008a2-107">[içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="008a2-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="008a2-108">.NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="008a2-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="008a2-109">Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.</span><span class="sxs-lookup"><span data-stu-id="008a2-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="008a2-110">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="008a2-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="008a2-111">Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="008a2-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="008a2-112">Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve aşağıda `STARTUP_LOADER_SAFEMODE` açıklandığı `flags` gibi parametre için bir değer geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="008a2-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="008a2-113">Arayan için `pwszVersion`null belirtirse, çalışma zamanının en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="008a2-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="008a2-114">Null'u geçmek, ana bilgisayara çalışma zamanının hangi sürümünün yüklendiği üzerinde hiçbir denetim vermez.</span><span class="sxs-lookup"><span data-stu-id="008a2-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="008a2-115">Bu yaklaşım bazı senaryolarda uygun olsa da, ana bilgisayara yüklemek için belirli bir sürüm sağlaması önerilir.</span><span class="sxs-lookup"><span data-stu-id="008a2-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="008a2-116">[içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="008a2-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="008a2-117">Geçerli değerler `svr` `wks`ve .</span><span class="sxs-lookup"><span data-stu-id="008a2-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="008a2-118">Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.</span><span class="sxs-lookup"><span data-stu-id="008a2-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="008a2-119">Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="008a2-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="008a2-120">Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile.</span><span class="sxs-lookup"><span data-stu-id="008a2-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="008a2-121">Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `flags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="008a2-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="008a2-122">[içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass.</span><span class="sxs-lookup"><span data-stu-id="008a2-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="008a2-123">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="008a2-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="008a2-124">[içinde] İstenen `IID` arabirimin `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="008a2-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="008a2-125">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="008a2-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="008a2-126">[çıkış] Döndürülen arabirim `riid`işaretçisi .</span><span class="sxs-lookup"><span data-stu-id="008a2-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="008a2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="008a2-127">Remarks</span></span>  
 <span data-ttu-id="008a2-128">Var `pwszVersion` olmayan bir çalışma zamanı sürümü belirtirse, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD Bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="008a2-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="008a2-129">Yürütme Bağlamı ve Windows Kimliğinin Akışı</span><span class="sxs-lookup"><span data-stu-id="008a2-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="008a2-130">CLR'nin sürüm <xref:System.Security.Principal.WindowsIdentity> 1'inde, nesne yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri aramaları gibi eşzamanlı noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="008a2-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="008a2-131">CLR'nin sürüm 2.0'ında, bir <xref:System.Threading.ExecutionContext> nesne şu anda çalıştırılamakta olan iş parçacığı yla ilgili bazı bilgileri sarar ve uygulama etki alanı sınırları boyunca değil, herhangi bir eşzamanlı nokta boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="008a2-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="008a2-132">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir asynchronous noktası boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="008a2-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="008a2-133">Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme, varsa, çok akar.</span><span class="sxs-lookup"><span data-stu-id="008a2-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="008a2-134">Akışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="008a2-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="008a2-135">İş parçacığı <xref:System.Threading.ExecutionContext> başına akışı bastırmak için ayarları değiştirerek (bkz. <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="008a2-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="008a2-136">İşlem varsayılan modunu, geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> ayarlardan bağımsız olarak nesnenin herhangi bir eşyoknom noktası boyunca akmayan sürüm 1 uyumluluk moduna değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="008a2-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="008a2-137">Varsayılan modu nasıl değiştirdiğiniz, CLR'yi yüklemek için yönetilen bir yürütülebilir veya yönetilmeyen bir barındırma arabirimi kullanıp kullanmadığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="008a2-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="008a2-138">Yönetilen yürütülebilir ler için `enabled` [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="008a2-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="008a2-139">Yönetilmeyen barındırma arabirimleri `STARTUP_LEGACY_IMPERSONATION` `flags` `CorBindToRuntimeEx` için, işlevi ararken parametredeki bayrağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="008a2-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="008a2-140">Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="008a2-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="008a2-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="008a2-141">Remarks</span></span>  
 <span data-ttu-id="008a2-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` ve aynı işlemi gerçekleştirmek, ancak `CorBindToRuntimeEx` işlev CLR davranışını belirtmek için bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="008a2-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="008a2-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="008a2-143">Requirements</span></span>  
 <span data-ttu-id="008a2-144">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="008a2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="008a2-145">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="008a2-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="008a2-146">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="008a2-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="008a2-147">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="008a2-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008a2-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="008a2-148">See also</span></span>

- [<span data-ttu-id="008a2-149">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="008a2-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="008a2-150">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="008a2-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="008a2-151">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="008a2-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="008a2-152">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="008a2-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="008a2-153">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="008a2-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="008a2-154">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="008a2-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
