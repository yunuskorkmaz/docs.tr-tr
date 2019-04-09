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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05ff93f9dc7e875c9f84dd6d8d1f4be9b4f12653
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153978"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="02d4d-102">STARTUP_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="02d4d-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="02d4d-103">Ortak dil çalışma zamanı (CLR) başlangıç davranışını gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="02d4d-104">Varsayılan olarak, atık toplama eşzamanlı olmayan ve yalnızca temel sınıf kitaplığı alan-bağımsız alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d4d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02d4d-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="02d4d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02d4d-106">Members</span></span>  
  
|<span data-ttu-id="02d4d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="02d4d-107">Member</span></span>|<span data-ttu-id="02d4d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02d4d-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="02d4d-109">Eş zamanlı çöp toplama kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="02d4d-110">İş istasyonu yapısı ve eşzamanlı olmayan çöp toplama çağıran bir tek işlemcili makinede sunucu yapısı ve eşzamanlı çöp toplama için isterse, bunun yerine çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="02d4d-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="02d4d-111">**Not:**  Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü.</span><span class="sxs-lookup"><span data-stu-id="02d4d-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="02d4d-112">64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="02d4d-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="02d4d-113">Yükleyici iyileştirmesi yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="02d4d-114">Hiçbir derlemeyi etki alanından bağımsız olarak yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="02d4d-115">Tüm derlemelerin etki alanından bağımsız olarak yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="02d4d-116">Güçlü adlı tüm derlemelerin etki alanından bağımsız yüklendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="02d4d-117">CLR sürümü ilkesinin geçilen sürüme uygulanmaz olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="02d4d-118">CLR belirtilen tam sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="02d4d-119">Dolgu en yeni uyumlu sürümü belirlemek üzere ilkeyi değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="02d4d-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="02d4d-120">Tercih edilen çalışma zamanı ayarlanacağını ancak başlatılmayacağını olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="02d4d-121">Sunucu çöp toplama kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="02d4d-122">Çöp toplamanın kullanılan sanal adresi tutacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="02d4d-123">Bir barındırma arabiriminin karıştırılmasına izin verilmeyeceğini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="02d4d-124">Kimliğe bürünme arasında zaman uyumsuz noktalar varsayılan olarak akmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="02d4d-125">İş parçacığı çalışmaya başladığında iş parçacığı yığınının tamamının taahhüt gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="02d4d-126">Yönetilen kimliğe bürünmelerin ve platform gerçekleştirilen çağırma belirtir bürünmelerin zaman uyumsuz noktalar arasında.</span><span class="sxs-lookup"><span data-stu-id="02d4d-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="02d4d-127">Varsayılan olarak, yalnızca yönetilen kimliğe bürünmeler uyumsuz noktalarda akacaktır.</span><span class="sxs-lookup"><span data-stu-id="02d4d-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="02d4d-128">Sistem belleği yetersiz olduğunda çöp toplamanın daha az kaydedilmiş alan kullanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="02d4d-129">Bkz: `gcTrimCommitOnLowMemory` içinde [paylaşılan Web barındırma için iyileştirme](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="02d4d-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="02d4d-130">Ortak dil çalışma zamanı olayları için olay izleme için Windows (ETW) etkinleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="02d4d-131">Bu bayrağın hiçbir etkisi için Windows Vista ile başlayarak, olay izleme her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="02d4d-132">Bkz: [.NET Framework günlük kaydını denetleme](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="02d4d-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="02d4d-133">Uygulama etki alanı kaynak izlemesinin etkin olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02d4d-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="02d4d-134">Bkz: <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliği ve [ \<appDomainResourceMonitoring > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="02d4d-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02d4d-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02d4d-135">Requirements</span></span>  
 <span data-ttu-id="02d4d-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02d4d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02d4d-137">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02d4d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02d4d-138">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02d4d-138">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="02d4d-139">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="02d4d-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02d4d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02d4d-140">See also</span></span>

- [<span data-ttu-id="02d4d-141">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="02d4d-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
