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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176493"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="a6d27-102">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6d27-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="a6d27-103">Ana bilgisayarların ortak dil çalışma zamanının (CLR) belirli bir sürümünü bir işleme yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6d27-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="a6d27-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6d27-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6d27-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a6d27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6d27-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="a6d27-107">[içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6d27-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="a6d27-108">.NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="a6d27-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="a6d27-109">Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.</span><span class="sxs-lookup"><span data-stu-id="a6d27-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="a6d27-110">CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a6d27-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="a6d27-111">Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="a6d27-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="a6d27-112">Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve parametre için `startupFlags` STARTUP_LOADER_SAFEMODE değerini geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a6d27-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="a6d27-113">Yöntem `pwszVersion` `null,` ise CLR herhangi bir sürümünü yüklemez.</span><span class="sxs-lookup"><span data-stu-id="a6d27-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="a6d27-114">Bunun yerine, çalışma süresini yüklemeyi başaramadıCLR_E_SHIM_RUNTIMELOAD döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6d27-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="a6d27-115">[içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6d27-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="a6d27-116">Geçerli değerler `svr` `wks`ve .</span><span class="sxs-lookup"><span data-stu-id="a6d27-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="a6d27-117">Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.</span><span class="sxs-lookup"><span data-stu-id="a6d27-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="a6d27-118">Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a6d27-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="a6d27-119">Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile.</span><span class="sxs-lookup"><span data-stu-id="a6d27-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="a6d27-120">Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `startupFlags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a6d27-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6d27-121">Intel Itanium mimarisini (eski adıyla IA-64) uygulayan 64 bit sistemlerde WOW64 x86 emülatörü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a6d27-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="a6d27-122">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için [32 bit Uygulamaları Çalıştırma'ya](/windows/desktop/WinProg64/running-32-bit-applications)bakın.</span><span class="sxs-lookup"><span data-stu-id="a6d27-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="a6d27-123">[içinde] ClR'nin yüklenmesi için sürümünü belirten bir ana bilgisayar yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="a6d27-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="a6d27-124">Dosya adı tam nitelikli bir yol içermiyorsa, dosyanın aramayı yapan yürütülebilir ile aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a6d27-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="a6d27-125">[içinde] Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6d27-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a6d27-126">[içinde] Eşzamanlı çöp toplama, etki alanı nötr kod ve `pwszVersion` parametre davranışını kontrol eden bayraklar kümesi.</span><span class="sxs-lookup"><span data-stu-id="a6d27-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="a6d27-127">Bayrak ayarlıdeğilse varsayılan değer tek alan adıdır.</span><span class="sxs-lookup"><span data-stu-id="a6d27-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="a6d27-128">Desteklenen değerlerin listesi için [numaralandırmaSTARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a6d27-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a6d27-129">[içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass.</span><span class="sxs-lookup"><span data-stu-id="a6d27-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a6d27-130">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a6d27-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a6d27-131">[içinde] `IID` İstediğinin arayüzü.</span><span class="sxs-lookup"><span data-stu-id="a6d27-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="a6d27-132">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a6d27-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a6d27-133">[çıkış] Yüklenen çalışma zamanı sürümüne bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a6d27-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6d27-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6d27-134">Requirements</span></span>  
 <span data-ttu-id="a6d27-135">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6d27-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6d27-136">**Üstbilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a6d27-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a6d27-137">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6d27-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6d27-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6d27-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d27-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d27-139">See also</span></span>

- [<span data-ttu-id="a6d27-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6d27-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="a6d27-141">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6d27-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="a6d27-142">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6d27-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="a6d27-143">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6d27-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="a6d27-144">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6d27-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="a6d27-145">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a6d27-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
