---
title: "STARTUP_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ca2db0cd7082a596999f1d74c9092264a65692ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS Numaralandırması
Ortak dil çalışma zamanı (CLR) başlangıç davranışını belirtmek değerlerini içerir. Varsayılan olarak, atık toplama eşzamanlı olmayan ve yalnızca temel sınıf kitaplığı etki alanı Tarafsız alanına yüklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Eşzamanlı atık toplama kullanılması gerektiğini belirtir. Eşzamansız atık toplama ve iş istasyonu yapı çağıran bir tek işlemcili makinede eşzamanlı atık toplama ve server yapı için isterse, bunun yerine çalıştırılır. **Not:** eşzamanlı atık toplama WOW64 çalışmakta olan uygulamalar desteklenmez x86 (eski adıyla IA-64) Intel Itanium mimarisi uygulama 64 bitlik sistemlerde öykünücüsü. 64-bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz: [çalıştıran 32-bit uygulamalar](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Bu yükleyici iyileştirme ortaya belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Hiçbir derlemeler etki alanı bağımsız olarak yüklü olduğunu belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Etki alanı bağımsız olarak tüm derlemelerde yüklenir belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Tanımlayıcı adlı derlemeler tüm etki alanı bağımsız yüklenen belirtir.|  
|`STARTUP_LOADER_SAFEMODE`|CLR sürümü İlkesi geçirilen sürümüne uygulanmaz olduğunu belirtir. CLR belirtilen tam sürümü yüklenir. Dolgu uyumlu en son sürümünü belirlemek için ilke değerlendirmez.|  
|`STARTUP_LOADER_SETPREFERENCE`|Tercih edilen çalışma zamanı ayarlayın, ancak aslında başlatılan belirtir.|  
|`STARTUP_SERVER_GC`|Sunucu çöp toplama kullanılacak belirtir.|  
|`STARTUP_HOARD_GC_VM`|Çöp toplama kullanılan sanal adres tutar belirtir.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Bir barındırma arabirimi karıştırma izin verilmeyeceğini olduğunu belirtir.|  
|`STARTUP_LEGACY_IMPERSONATION`|Kimliğe bürünme zaman uyumsuz noktaları arasında varsayılan olarak akışını değil belirtir.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|İş parçacığı çalışmaya başladığında tam iş parçacığı yığın taahhüt olmamalıdır olduğunu belirtir.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Yönetilen impersonations ve impersonations platformu ile elde edecek çağırma belirtir akış zaman uyumsuz noktaları arasında. Varsayılan olarak, yalnızca yönetilen impersonations zaman uyumsuz noktaları arasında akar.|  
|`STARTUP_TRIM_GC_COMMIT`|Çöp toplama sistem bellek düşük olduğunda daha az kaydedilmiş alan kullanacağını belirtir. Bkz: `gcTrimCommitOnLowMemory` içinde [paylaşılan Web barındırma için iyileştirme](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Ortak dil çalışma zamanı olayları için olay izleme için Windows (ETW) etkinleştirilip etkinleştirilmediğini belirtir. Bu bayrak etkisizdir şekilde Windows Vista ile başlayarak, olay izleme her zaman etkindir. Bkz: [.NET Framework günlük kaydını denetleme](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Uygulama etki alanı kaynak izleme etkin olduğunu belirtir. Bkz: <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliği ve [ \<appDomainResourceMonitoring > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
