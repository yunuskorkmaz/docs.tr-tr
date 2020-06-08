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
ms.openlocfilehash: 9d1c7f4f5b881f7f55539602c152b557a7950472
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504413"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="f6286-102">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6286-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="f6286-103">Ana bilgisayarların belirli bir ortak dil çalışma zamanı (CLR) sürümünü bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6286-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="f6286-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f6286-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6286-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f6286-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f6286-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6286-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="f6286-107">'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="f6286-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="f6286-108">.NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="f6286-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="f6286-109">Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="f6286-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="f6286-110">CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f6286-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="f6286-111">Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="f6286-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="f6286-112">Bir konak, bu dolgunun ilke değerlendirmesini atlamasını ve ' de `pwszVersion` parametre için bir STARTUP_LOADER_SAFEMODE değeri geçirerek belirtilen tam sürümü yüklemesini zorunlu hale getirebilirsiniz `startupFlags` .</span><span class="sxs-lookup"><span data-stu-id="f6286-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="f6286-113">`pwszVersion`, `null,` Yöntemi clr 'nin herhangi bir sürümünü yüklemez.</span><span class="sxs-lookup"><span data-stu-id="f6286-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="f6286-114">Bunun yerine, çalışma zamanını yükleyemediğini belirten CLR_E_SHIM_RUNTIMELOAD döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6286-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="f6286-115">'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f6286-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="f6286-116">Geçerli değerler `svr` ve ' dir `wks` .</span><span class="sxs-lookup"><span data-stu-id="f6286-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="f6286-117">Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6286-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="f6286-118">`pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f6286-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="f6286-119">Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` .</span><span class="sxs-lookup"><span data-stu-id="f6286-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="f6286-120">Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `startupFlags` ), sunucu derlemesi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f6286-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6286-121">Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f6286-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="f6286-122">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="f6286-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="f6286-123">'ndaki Yüklenecek CLR sürümünü belirten bir ana bilgisayar yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f6286-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="f6286-124">Dosya adı tam nitelikli bir yol içermiyorsa, dosyanın çağrıyı yapan çalıştırılabilirle aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f6286-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="f6286-125">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6286-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f6286-126">'ndaki Eşzamanlı çöp toplamayı, etki alanını bağımsız kodu ve parametresinin davranışını denetleyen bir bayrak kümesi `pwszVersion` .</span><span class="sxs-lookup"><span data-stu-id="f6286-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="f6286-127">Hiçbir bayrak ayarlanmamışsa varsayılan, tek etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="f6286-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="f6286-128">Desteklenen değerlerin listesi için bkz. [startup_flags numaralandırması](startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f6286-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f6286-129">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="f6286-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f6286-130">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f6286-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f6286-131">'ndaki `IID`İstediğiniz arabirim.</span><span class="sxs-lookup"><span data-stu-id="f6286-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="f6286-132">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f6286-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f6286-133">dışı Yüklenen çalışma zamanının sürümüne yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f6286-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6286-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6286-134">Requirements</span></span>  
 <span data-ttu-id="f6286-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6286-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6286-136">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="f6286-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f6286-137">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f6286-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6286-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6286-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6286-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6286-139">See also</span></span>

- [<span data-ttu-id="f6286-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6286-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="f6286-141">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6286-141">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="f6286-142">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6286-142">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="f6286-143">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6286-143">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="f6286-144">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6286-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="f6286-145">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f6286-145">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
