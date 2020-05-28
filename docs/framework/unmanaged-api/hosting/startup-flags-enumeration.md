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
ms.openlocfilehash: b4694efffa0a3dd6fed1f97fc2359c5eb335d440
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006421"
---
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS Numaralandırması
Ortak dil çalışma zamanının (CLR) başlangıç davranışını gösteren değerleri içerir. Varsayılan olarak, atık toplama eşzamanlı değildir ve yalnızca temel sınıf kitaplığı, etki alanı nötr alanına yüklenir.  
  
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
|`STARTUP_CONCURRENT_GC`|Eşzamanlı atık toplamanın kullanılması gerektiğini belirtir. Arayan, tek işlemcili bir makinede sunucu derlemesini ve eşzamanlı atık toplamayı isterse, bunun yerine iş istasyonu oluşturma ve eşzamanlı olmayan çöp toplama çalıştırılır. **Note:**  Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Yükleyici iyileştirmesinin gerçekleşeceğini belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Etki alanı nötr olarak hiçbir derlemenin yüklenmediğini belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Tüm derlemelerin etki alanından bağımsız olarak yüklendiğini belirtir.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Tüm tanımlayıcı adlı derlemelerin etki alanı nötr olarak yüklendiğini belirtir.|  
|`STARTUP_LOADER_SAFEMODE`|CLR sürüm ilkesinin geçirilen sürüme uygulanmayacak olduğunu belirtir. CLR 'nin belirtilen tam sürümü yüklenir. Dolgu, en son uyumlu sürümü belirlemede ilkeyi değerlendirmez.|  
|`STARTUP_LOADER_SETPREFERENCE`|Tercih edilen çalışma zamanının ayarlanacağını ancak gerçekten başlatıllamayacağını belirtir.|  
|`STARTUP_SERVER_GC`|Sunucu çöp toplama işleminin kullanılacağını belirtir.|  
|`STARTUP_HOARD_GC_VM`|Çöp toplamanın kullanılan sanal adresi tutacaksınız.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Barındırma arabirimini karıştırmaya izin verilmeyeceğini belirtir.|  
|`STARTUP_LEGACY_IMPERSONATION`|Kimliğe bürünme özelliğinin, varsayılan olarak zaman uyumsuz noktalara akmamalıdır belirtir.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Tam iş parçacığı yığınının iş parçacığı çalışmaya başladığında uygulanmamalıdır.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Platform çağırma aracılığıyla elde edilen yönetilen ımpersonations ve ımpersontiklerde zaman uyumsuz noktalarda akacağı belirtir. Varsayılan olarak, yalnızca yönetilen ımpersontiklerde zaman uyumsuz noktalarda akış yapılır.|  
|`STARTUP_TRIM_GC_COMMIT`|Çöp toplamanın sistem belleği azaldığında daha az işlenmiş alan kullanacağınızı belirtir. Bkz `gcTrimCommitOnLowMemory` . [Paylaşılan Web barındırma için iyileştirme](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Windows için olay izlemenin (ETW) ortak dil çalışma zamanı olayları için etkinleştirildiğini belirtir. Windows Vista ile başlayarak, olay izleme her zaman etkindir, bu nedenle bu bayrağın bir etkisi yoktur. Bkz. [.NET Framework günlüğünü denetleme](../../performance/controlling-logging.md).|  
|`STARTUP_ARM`|Uygulama etki alanı kaynak izlemenin etkinleştirildiğini belirtir. Bkz <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> . özelliği ve [ \<appDomainResourceMonitoring> öğesi](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
