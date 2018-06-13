---
title: CorBindToRuntimeHost İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c1d83b32402343f3cd2b5403e328698abd6a930
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436221"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="5040b-102">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="5040b-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="5040b-103">Süreç içine ortak dil çalışma zamanı (CLR) belirtilen bir sürümünü yüklemek ana bilgisayarları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5040b-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="5040b-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5040b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5040b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5040b-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5040b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5040b-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="5040b-107">[in] Yüklemek istediğiniz CLR sürümü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="5040b-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="5040b-108">.NET Framework sürüm numarası noktalarla ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="5040b-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="5040b-109">Dize olarak geçirilen `pwszVersion` sürüm numarası (örneğin, "v1.0.1529") ilk üç bölümleri tarafından izlenen "v" karakter ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5040b-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="5040b-110">CLR bazı sürümleri CLR önceki sürümleriyle uyumluluk belirten bir ilke bildirimi ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5040b-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="5040b-111">Varsayılan olarak, başlatma dolgusu değerlendirir `pwszVersion` ilke deyimleri ve yükleri karşı çalışma zamanı en son sürümü olan istenen sürümü ile uyumlu.</span><span class="sxs-lookup"><span data-stu-id="5040b-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="5040b-112">Bir ana bilgisayar ilkesi değerlendirmesi atlayın ve belirtilen tam sürümünü yüklemek için dolgu zorlayabilirsiniz `pwszVersion` için STARTUP_LOADER_SAFEMODE değerini geçirerek `startupFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5040b-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="5040b-113">Varsa `pwszVersion` olan `null,` yöntemi herhangi bir CLR sürümü yüklemez.</span><span class="sxs-lookup"><span data-stu-id="5040b-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="5040b-114">Bunun yerine, çalışma zamanı yükleme başarısız olduğunu gösteren CLR_E_SHIM_RUNTIMELOAD döndürür.</span><span class="sxs-lookup"><span data-stu-id="5040b-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="5040b-115">[in] Sunucu veya CLR iş istasyonu yapı yük belirtir bir dize.</span><span class="sxs-lookup"><span data-stu-id="5040b-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="5040b-116">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="5040b-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="5040b-117">Server yapı çöp koleksiyonları için birden çok işlemci yararlanmak için optimize edilmiştir ve iş istasyonu yapı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5040b-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="5040b-118">Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derleme yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5040b-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="5040b-119">Bir tek işlemcili makine üzerinde çalışan iş istasyonu derleme her zaman yüklenir, olsa bile `pwszBuildFlavor` ayarlanır `svr`.</span><span class="sxs-lookup"><span data-stu-id="5040b-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="5040b-120">Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı atık toplama belirtilir (açıklamasına bakın `startupFlags` parametresi), sunucu derleme yüklendi.</span><span class="sxs-lookup"><span data-stu-id="5040b-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5040b-121">Eşzamanlı atık toplama WOW64 çalışan uygulamalarda desteklenmiyor x86 (eski adıyla IA-64) Intel Itanium mimarisi uygulama 64 bitlik sistemlerde öykünücüsü.</span><span class="sxs-lookup"><span data-stu-id="5040b-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="5040b-122">64-bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz: [çalıştıran 32-bit uygulamalar](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="5040b-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="5040b-123">[in] Yüklemek için CLR sürümü belirten bir ana bilgisayar yapılandırma dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="5040b-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="5040b-124">Dosya adı tam nitelenmiş bir yol içermiyorsa, dosyanın çağrıyı yapan yürütülebilir dosya ile aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5040b-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="5040b-125">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5040b-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="5040b-126">[in] Eşzamanlı atık toplama, etki alanı Tarafsız kodu ve davranışını denetleyen bayrakları kümesi `pwszVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5040b-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="5040b-127">Hiçbir bayrağı ayarlandıysa, varsayılan tek etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="5040b-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="5040b-128">Desteklenen değerler listesi için bkz: [STARTUP_FLAGS numaralandırması](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5040b-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="5040b-129">[in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5040b-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="5040b-130">Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5040b-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="5040b-131">[in] `IID` İsteyen arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5040b-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="5040b-132">Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5040b-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="5040b-133">[out] Yüklenen çalışma zamanı sürümü için bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5040b-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5040b-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5040b-134">Requirements</span></span>  
 <span data-ttu-id="5040b-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5040b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5040b-136">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="5040b-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5040b-137">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5040b-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5040b-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5040b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5040b-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5040b-139">See Also</span></span>  
 [<span data-ttu-id="5040b-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="5040b-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="5040b-141">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="5040b-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="5040b-142">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="5040b-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="5040b-143">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="5040b-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="5040b-144">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5040b-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="5040b-145">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5040b-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
