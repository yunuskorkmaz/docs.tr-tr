---
title: "STARTUP_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: STARTUP_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: STARTUP_FLAGS
helpviewer_keywords: STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca2db0cd7082a596999f1d74c9092264a65692ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="45852-102">STARTUP_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="45852-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="45852-103">Ortak dil çalışma zamanı (CLR) başlangıç davranışını belirtmek değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="45852-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="45852-104">Varsayılan olarak, atık toplama eşzamanlı olmayan ve yalnızca temel sınıf kitaplığı etki alanı Tarafsız alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="45852-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45852-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45852-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="45852-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="45852-106">Members</span></span>  
  
|<span data-ttu-id="45852-107">Üye</span><span class="sxs-lookup"><span data-stu-id="45852-107">Member</span></span>|<span data-ttu-id="45852-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45852-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="45852-109">Eşzamanlı atık toplama kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="45852-110">Eşzamansız atık toplama ve iş istasyonu yapı çağıran bir tek işlemcili makinede eşzamanlı atık toplama ve server yapı için isterse, bunun yerine çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="45852-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="45852-111">**Not:** eşzamanlı atık toplama WOW64 çalışmakta olan uygulamalar desteklenmez x86 (eski adıyla IA-64) Intel Itanium mimarisi uygulama 64 bitlik sistemlerde öykünücüsü.</span><span class="sxs-lookup"><span data-stu-id="45852-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="45852-112">64-bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz: [çalıştıran 32-bit uygulamalar](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="45852-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="45852-113">Bu yükleyici iyileştirme ortaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="45852-114">Hiçbir derlemeler etki alanı bağımsız olarak yüklü olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="45852-115">Etki alanı bağımsız olarak tüm derlemelerde yüklenir belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="45852-116">Tanımlayıcı adlı derlemeler tüm etki alanı bağımsız yüklenen belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="45852-117">CLR sürümü İlkesi geçirilen sürümüne uygulanmaz olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="45852-118">CLR belirtilen tam sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="45852-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="45852-119">Dolgu uyumlu en son sürümünü belirlemek için ilke değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="45852-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="45852-120">Tercih edilen çalışma zamanı ayarlayın, ancak aslında başlatılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="45852-121">Sunucu çöp toplama kullanılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="45852-122">Çöp toplama kullanılan sanal adres tutar belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="45852-123">Bir barındırma arabirimi karıştırma izin verilmeyeceğini olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="45852-124">Kimliğe bürünme zaman uyumsuz noktaları arasında varsayılan olarak akışını değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="45852-125">İş parçacığı çalışmaya başladığında tam iş parçacığı yığın taahhüt olmamalıdır olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="45852-126">Yönetilen impersonations ve impersonations platformu ile elde edecek çağırma belirtir akış zaman uyumsuz noktaları arasında.</span><span class="sxs-lookup"><span data-stu-id="45852-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="45852-127">Varsayılan olarak, yalnızca yönetilen impersonations zaman uyumsuz noktaları arasında akar.</span><span class="sxs-lookup"><span data-stu-id="45852-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="45852-128">Çöp toplama sistem bellek düşük olduğunda daha az kaydedilmiş alan kullanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="45852-129">Bkz: `gcTrimCommitOnLowMemory` içinde [paylaşılan Web barındırma için iyileştirme](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="45852-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="45852-130">Ortak dil çalışma zamanı olayları için olay izleme için Windows (ETW) etkinleştirilip etkinleştirilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="45852-131">Bu bayrak etkisizdir şekilde Windows Vista ile başlayarak, olay izleme her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="45852-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="45852-132">Bkz: [.NET Framework günlük kaydını denetleme](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="45852-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="45852-133">Uygulama etki alanı kaynak izleme etkin olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45852-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="45852-134">Bkz: <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliği ve [ \<appDomainResourceMonitoring > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="45852-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45852-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45852-135">Requirements</span></span>  
 <span data-ttu-id="45852-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45852-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45852-137">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45852-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45852-138">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45852-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45852-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45852-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45852-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45852-140">See Also</span></span>  
 [<span data-ttu-id="45852-141">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="45852-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
