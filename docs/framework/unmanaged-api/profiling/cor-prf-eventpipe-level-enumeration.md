---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_LEVEL numaralandırması'
title: COR_PRF_EVENTPIPE_LEVEL numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_LEVEL
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: da8211da1a9bb6262b078c5e56bee1d0c1f9342e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805824"
---
# <a name="cor_prf_eventpipe_level-enumeration"></a>COR_PRF_EVENTPIPE_LEVEL numaralandırması

Bir EventPipe olayının düzeyini açıklar.
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_LOGALWAYS = 0,
    COR_PRF_EVENTPIPE_CRITICAL = 1,
    COR_PRF_EVENTPIPE_ERROR = 2,
    COR_PRF_EVENTPIPE_WARNING = 3,
    COR_PRF_EVENTPIPE_INFORMATIONAL = 4,
    COR_PRF_EVENTPIPE_VERBOSE = 5
} COR_PRF_EVENTPIPE_LEVEL;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|Olay her zaman günlüğe kaydedilir.|
|`COR_PRF_EVENTPIPE_CRITICAL`|Olay, kritik bir iletiyi temsil eder.|
|`COR_PRF_EVENTPIPE_ERROR`|Olay bir hata iletisini temsil eder.|
|`COR_PRF_EVENTPIPE_WARNING`|Olay bir uyarı iletisini temsil eder.|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|Olay bir bilgi iletisini temsil eder.|
|`COR_PRF_EVENTPIPE_VERBOSE`|Olay, ayrıntılı bir iletiyi temsil eder.|
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_EVENTPIPE_LEVEL`Numaralandırma, tanımlanmakta olan olayın düzeyini göstermek Için [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) yöntemi tarafından kullanılır.
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
- [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md)
