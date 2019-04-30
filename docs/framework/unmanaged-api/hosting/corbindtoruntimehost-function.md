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
ms.openlocfilehash: f88c22f88aa9e1aaa777f12d8b230e7ba92dffeb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774588"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="04785-102">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="04785-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="04785-103">Bir işleme belirtilen bir ortak dil çalışma zamanı (CLR) sürümünü yüklemek için ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="04785-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="04785-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04785-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04785-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04785-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="04785-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04785-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="04785-107">[in] Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="04785-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="04785-108">.NET Framework uygulamasındaki sürüm numarası noktayla ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="04785-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="04785-109">Olarak geçen dize `pwszVersion` (örneğin, "v1.0.1529") sürüm numarasının ilk üç parçalar tarafından izlenen "v" karakteriyle başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="04785-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="04785-110">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="04785-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="04785-111">Varsayılan olarak, başlangıç dolgusu değerlendirir `pwszVersion` ilke bildirimlerine ve yükleri karşı çalışma zamanının en son sürümü olan istenen sürümle uyumlu.</span><span class="sxs-lookup"><span data-stu-id="04785-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="04785-112">Bir konak ilke değerlendirmesini atlamaya ve belirtilen tam sürümü yüklemeye zorlayabilir `pwszVersion` STARTUP_LOADER_SAFEMODE değerini geçirerek `startupFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="04785-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="04785-113">Varsa `pwszVersion` olduğu `null,` yöntem CLR'nin herhangi bir sürümünü yüklemez.</span><span class="sxs-lookup"><span data-stu-id="04785-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="04785-114">Bunun yerine çalışma zamanının başarısız olduğunu gösteren CLR_E_SHIM_RUNTIMELOAD döndürür.</span><span class="sxs-lookup"><span data-stu-id="04785-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="04785-115">[in] Sunucunun veya CLR çalışma istasyonu yapısı yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="04785-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="04785-116">Geçerli değerler `svr` ve `wks`.</span><span class="sxs-lookup"><span data-stu-id="04785-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="04785-117">Sunucu yapısı çöp toplama için birden çok işlemciden yararlanmak için optimize edilmiştir ve çalışma istasyonu yapısı tek işlemcili makinede çalışan istemci uygulamaları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="04785-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="04785-118">Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="04785-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="04785-119">İş istasyonu yapısı, bir tek işlemcili makinede çalışırken daima yüklenir, bile `pwszBuildFlavor` ayarlanır `svr`.</span><span class="sxs-lookup"><span data-stu-id="04785-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="04785-120">Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eş zamanlı çöp toplama belirtilmişse (açıklamasına bakın `startupFlags` parametresi), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="04785-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04785-121">Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü.</span><span class="sxs-lookup"><span data-stu-id="04785-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="04785-122">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="04785-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="04785-123">[in] Yüklenecek CLR sürümünü belirten ana bilgisayar yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="04785-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="04785-124">Dosya adı tam nitelenmiş bir yol içermiyorsa, dosyanın çağrıyı yapan yürütülebilir olarak aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="04785-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="04785-125">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="04785-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="04785-126">[in] Eş zamanlı çöp toplama, alan-bağımsız kod ve davranışını denetleyen bayrak kümesi `pwszVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="04785-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="04785-127">Varsayılan, hiçbir bayrak ayarlanmışsa tek etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="04785-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="04785-128">Desteklenen değerler listesi için bkz. [STARTUP_FLAGS numaralandırma](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="04785-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="04785-129">[in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="04785-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="04785-130">Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="04785-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="04785-131">[in] `IID` Arabirimin istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="04785-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="04785-132">Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="04785-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="04785-133">[out] Yüklenen çalışma zamanı sürümü için bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="04785-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04785-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04785-134">Requirements</span></span>  
 <span data-ttu-id="04785-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04785-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04785-136">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="04785-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="04785-137">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04785-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04785-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04785-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04785-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04785-139">See also</span></span>

- [<span data-ttu-id="04785-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="04785-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="04785-141">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="04785-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="04785-142">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="04785-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="04785-143">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="04785-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="04785-144">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04785-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="04785-145">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="04785-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
