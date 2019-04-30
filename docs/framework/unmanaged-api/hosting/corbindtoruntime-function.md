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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb5c05a88c12b5124c77b0d0a7f834b405dd289f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697426"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="3f559-102">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f559-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="3f559-103">Ortak dil çalışma zamanı (CLR) bir işleme yüklemek için yöneilmeyen ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="3f559-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="3f559-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f559-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f559-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f559-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f559-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f559-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="3f559-107">[in] Yüklemek istediğiniz CLR sürümünü tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="3f559-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="3f559-108">.NET Framework uygulamasındaki sürüm numarası noktayla ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="3f559-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="3f559-109">Olarak geçen dize `pwszVersion` (örneğin, "v1.0.1529") sürüm numarasının ilk üç parçalar tarafından izlenen "v" karakteriyle başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f559-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="3f559-110">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3f559-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="3f559-111">Varsayılan olarak, başlangıç dolgusu değerlendirir `pwszVersion` ilke bildirimlerine ve yükleri karşı çalışma zamanının en son sürümü olan istenen sürümle uyumlu.</span><span class="sxs-lookup"><span data-stu-id="3f559-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="3f559-112">Bir konak ilke değerlendirmesini atlamaya ve belirtilen tam sürümü yüklemeye zorlayabilir `pwszVersion` değerini geçirerek `STARTUP_LOADER_SAFEMODE` için `flags` aşağıda açıklandığı gibi parametre.</span><span class="sxs-lookup"><span data-stu-id="3f559-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="3f559-113">Arayan için null belirtiyorsa `pwszVersion`, çalışma zamanının en son sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="3f559-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="3f559-114">Null geçirme konak çalışma zamanının yüklendiği üzerinde hiçbir denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f559-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="3f559-115">Bu yaklaşım bazı senaryolarda uygun olsa da, konağın belirli bir sürümünü yüklemek için sağlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="3f559-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="3f559-116">[in] Sunucunun veya CLR çalışma istasyonu yapısı yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3f559-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="3f559-117">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="3f559-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="3f559-118">Sunucu yapısı çöp toplama için birden çok işlemciden yararlanmak için optimize edilmiştir ve çalışma istasyonu yapısı tek işlemcili makinede çalışan istemci uygulamaları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f559-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="3f559-119">Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3f559-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="3f559-120">İş istasyonu yapısı, bir tek işlemcili makinede çalışırken daima yüklenir, bile `pwszBuildFlavor` ayarlanır `svr`.</span><span class="sxs-lookup"><span data-stu-id="3f559-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="3f559-121">Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eş zamanlı çöp toplama belirtilmişse (açıklamasına bakın `flags` parametresi), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3f559-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3f559-122">[in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3f559-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3f559-123">Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="3f559-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3f559-124">[in] `IID` , İstenen arabiriminden `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="3f559-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="3f559-125">Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="3f559-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3f559-126">[out] Döndürülen arabirim işaretçisi `riid`.</span><span class="sxs-lookup"><span data-stu-id="3f559-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f559-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f559-127">Remarks</span></span>  
 <span data-ttu-id="3f559-128">Varsa `pwszVersion` mevcut değil, bir çalışma zamanı sürümünü belirten `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD bir HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f559-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="3f559-129">Yürütme bağlamı ve Windows Identity akışı</span><span class="sxs-lookup"><span data-stu-id="3f559-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="3f559-130">CLR sürüm 1 <xref:System.Security.Principal.WindowsIdentity> nesne yeni iş parçacığı, iş parçacığı havuzları ya da Zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalar arasında akış değil.</span><span class="sxs-lookup"><span data-stu-id="3f559-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="3f559-131">CLR 2.0 sürümünde bir <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığını hakkında bazı bilgiler sarmalar ve herhangi bir zaman uyumsuz noktası arasında ancak olmayan uygulama etki alanı sınırları üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="3f559-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="3f559-132">Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir zaman uyumsuz noktası üzerinden akar.</span><span class="sxs-lookup"><span data-stu-id="3f559-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="3f559-133">Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme varsa, çok akar.</span><span class="sxs-lookup"><span data-stu-id="3f559-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="3f559-134">Flow'a iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f559-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="3f559-135">Değiştirerek <xref:System.Threading.ExecutionContext> akışını bir iş parçacığı başına temelinde bastırmak için ayarları (bkz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="3f559-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="3f559-136">Sürüm 1 uyumluluk modu için varsayılan işlem modu değiştirerek burada <xref:System.Security.Principal.WindowsIdentity> nesne akan tüm zaman uyumsuz noktası üzerinden açmamasından <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3f559-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="3f559-137">Varsayılan mod nasıl değiştirmeniz mi yönetilen bir yürütülebilir dosya veya yönetilmeyen bir barındırma arabiriminin CLR'yi yüklemek için kullandığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="3f559-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="3f559-138">Yönetilen yürütülebilir dosyalar için ayarlamanız gerekir `enabled` özniteliği [ \<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="3f559-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="3f559-139">Yönetilmeyen barındırma arabirimleri için ayarlanan `STARTUP_LEGACY_IMPERSONATION` bayrağını `flags` çağırırken parametre `CorBindToRuntimeEx` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3f559-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="3f559-140">Sürüm 1 uyumluluk modu, tüm işlem ve işlemde tüm uygulama etki alanları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3f559-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f559-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f559-141">Remarks</span></span>  
 <span data-ttu-id="3f559-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirmek ancak `CorBindToRuntimeEx` işlevi CLR'nin davranışını belirtmek için bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f559-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f559-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f559-143">Requirements</span></span>  
 <span data-ttu-id="3f559-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f559-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f559-145">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f559-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f559-146">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f559-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f559-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f559-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f559-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f559-148">See also</span></span>

- [<span data-ttu-id="3f559-149">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f559-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3f559-150">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f559-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="3f559-151">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f559-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="3f559-152">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f559-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="3f559-153">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f559-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="3f559-154">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3f559-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
