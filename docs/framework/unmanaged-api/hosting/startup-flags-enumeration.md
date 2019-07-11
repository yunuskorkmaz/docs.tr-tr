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
ms.openlocfilehash: f254582d96b310c247778818fc0d5daaae0d911c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737268"
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS Numaralandırması
Ortak dil çalışma zamanı (CLR) başlangıç davranışını gösteren değerleri içerir. Varsayılan olarak, atık toplama eşzamanlı olmayan ve yalnızca temel sınıf kitaplığı alan-bağımsız alanına yüklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Eş zamanlı çöp toplama kullanılması gerektiğini belirtir. İş istasyonu yapısı ve eşzamanlı olmayan çöp toplama çağıran bir tek işlemcili makinede sunucu yapısı ve eşzamanlı çöp toplama için isterse, bunun yerine çalıştırılır. **Not:**  Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Yükleyici iyileştirmesi yapılacağını belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Hiçbir derlemeyi etki alanından bağımsız olarak yüklendiğini belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Tüm derlemelerin etki alanından bağımsız olarak yüklendiğini belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Güçlü adlı tüm derlemelerin etki alanından bağımsız yüklendiğini belirtir.|  
|`STARTUP_LOADER_SAFEMODE`|CLR sürümü ilkesinin geçilen sürüme uygulanmaz olduğunu belirtir. CLR belirtilen tam sürümü yüklenir. Dolgu en yeni uyumlu sürümü belirlemek üzere ilkeyi değerlendirmez.|  
|`STARTUP_LOADER_SETPREFERENCE`|Tercih edilen çalışma zamanı ayarlanacağını ancak başlatılmayacağını olduğunu belirtir.|  
|`STARTUP_SERVER_GC`|Sunucu çöp toplama kullanılması gerektiğini belirtir.|  
|`STARTUP_HOARD_GC_VM`|Çöp toplamanın kullanılan sanal adresi tutacağını belirtir.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Bir barındırma arabiriminin karıştırılmasına izin verilmeyeceğini olduğunu belirtir.|  
|`STARTUP_LEGACY_IMPERSONATION`|Kimliğe bürünme arasında zaman uyumsuz noktalar varsayılan olarak akmaması gerektiğini belirtir.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|İş parçacığı çalışmaya başladığında iş parçacığı yığınının tamamının taahhüt gerektiğini belirtir.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Yönetilen kimliğe bürünmelerin ve platform gerçekleştirilen çağırma belirtir bürünmelerin zaman uyumsuz noktalar arasında. Varsayılan olarak, yalnızca yönetilen kimliğe bürünmeler uyumsuz noktalarda akacaktır.|  
|`STARTUP_TRIM_GC_COMMIT`|Sistem belleği yetersiz olduğunda çöp toplamanın daha az kaydedilmiş alan kullanacağını belirtir. Bkz: `gcTrimCommitOnLowMemory` içinde [paylaşılan Web barındırma için iyileştirme](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Ortak dil çalışma zamanı olayları için olay izleme için Windows (ETW) etkinleştirildiğini belirtir. Bu bayrağın hiçbir etkisi için Windows Vista ile başlayarak, olay izleme her zaman etkindir. Bkz: [.NET Framework günlük kaydını denetleme](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Uygulama etki alanı kaynak izlemesinin etkin olduğunu belirtir. Bkz: <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliği ve [ \<appDomainResourceMonitoring > öğesi](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
