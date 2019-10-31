---
title: STARTUP_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
ms.openlocfilehash: 1799e0af91fa6074f174120b29e2302a27230c62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141461"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="ddc9c-102">STARTUP_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ddc9c-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="ddc9c-103">Ortak dil çalışma zamanının (CLR) başlangıç davranışını gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="ddc9c-104">Varsayılan olarak, atık toplama eşzamanlı değildir ve yalnızca temel sınıf kitaplığı, etki alanı nötr alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddc9c-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ddc9c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ddc9c-106">Members</span></span>  
  
|<span data-ttu-id="ddc9c-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ddc9c-107">Member</span></span>|<span data-ttu-id="ddc9c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc9c-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="ddc9c-109">Eşzamanlı atık toplamanın kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="ddc9c-110">Arayan, tek işlemcili bir makinede sunucu derlemesini ve eşzamanlı atık toplamayı isterse, bunun yerine iş istasyonu oluşturma ve eşzamanlı olmayan çöp toplama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="ddc9c-111">**Note:**  Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="ddc9c-112">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="ddc9c-113">Yükleyici iyileştirmesinin gerçekleşeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="ddc9c-114">Etki alanı nötr olarak hiçbir derlemenin yüklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="ddc9c-115">Tüm derlemelerin etki alanından bağımsız olarak yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="ddc9c-116">Tüm tanımlayıcı adlı derlemelerin etki alanı nötr olarak yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="ddc9c-117">CLR sürüm ilkesinin geçirilen sürüme uygulanmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="ddc9c-118">CLR 'nin belirtilen tam sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="ddc9c-119">Dolgu, en son uyumlu sürümü belirlemede ilkeyi değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="ddc9c-120">Tercih edilen çalışma zamanının ayarlanacağını ancak gerçekten başlatıllamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="ddc9c-121">Sunucu çöp toplama işleminin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="ddc9c-122">Çöp toplamanın kullanılan sanal adresi tutacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="ddc9c-123">Barındırma arabirimini karıştırmaya izin verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="ddc9c-124">Kimliğe bürünme özelliğinin, varsayılan olarak zaman uyumsuz noktalara akmamalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="ddc9c-125">Tam iş parçacığı yığınının iş parçacığı çalışmaya başladığında uygulanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="ddc9c-126">Platform çağırma aracılığıyla elde edilen yönetilen ımpersonations ve ımpersontiklerde zaman uyumsuz noktalarda akacağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="ddc9c-127">Varsayılan olarak, yalnızca yönetilen ımpersontiklerde zaman uyumsuz noktalarda akış yapılır.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="ddc9c-128">Çöp toplamanın sistem belleği azaldığında daha az işlenmiş alan kullanacağınızı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="ddc9c-129">Bkz. `gcTrimCommitOnLowMemory` [Paylaşılan Web barındırma Için iyileştirme](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="ddc9c-130">Windows için olay izlemenin (ETW) ortak dil çalışma zamanı olayları için etkinleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="ddc9c-131">Windows Vista ile başlayarak, olay izleme her zaman etkindir, bu nedenle bu bayrağın bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="ddc9c-132">Bkz. [.NET Framework günlüğünü denetleme](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="ddc9c-133">Uygulama etki alanı kaynak izlemenin etkinleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="ddc9c-134"><xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliğine ve [\<appDomainResourceMonitoring > öğesine](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ddc9c-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddc9c-135">Requirements</span></span>  
 <span data-ttu-id="ddc9c-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc9c-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ddc9c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ddc9c-138">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ddc9c-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddc9c-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc9c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc9c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-140">See also</span></span>

- [<span data-ttu-id="ddc9c-141">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ddc9c-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
