---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması'
title: COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PROVIDER_CONFIG
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2a7a5e720e9468b44e6504d24a3b9ad836e13693
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805850"
---
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a>COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması

Bir EventPipe sağlayıcısını yapılandırmak için gereken alanları açıklar.
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`providerName`|Etkinleştirilecek sağlayıcının adı.|  
|`keywords`|Sağlayıcıda etkinleştirilecek anahtar sözcükler.|  
|`loggingLevel`|Sağlayıcıda etkinleştirilecek düzey.|  
|`filterData`|Sağlayıcıyı etkinleştirirken kullanılacak filtreverileri içeren geniş bir karakter dizesi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_EVENTPIPE_PROVIDER_CONFIG`Yapı, oturuma eklenmekte olan sağlayıcının yapılandırmasını göstermek Için [ICorProfilerInfo12:: EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) yöntemi tarafından kullanılır.
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
- [ICorProfilerInfo12:: EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
