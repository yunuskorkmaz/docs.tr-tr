---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENT_DATA numaralandırması'
title: COR_PRF_EVENT_DATA numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENT_DATA
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 477f36476deb9c0d74e263703e36b134c91b5327
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805577"
---
# <a name="cor_prf_event_data-enumeration"></a>COR_PRF_EVENT_DATA numaralandırması

Yazılan bir EventPipe olayının olay verilerini açıklar.
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ptr`|Verilere yönelik bir işaretçi.|  
|`size`|Tarafından işaret edilen verilerin boyutu `ptr` .|  
|`reserved`|Ayrılmış uygulamaya özel alan.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_EVENT_DATA`Yapı, yazılan olayın veri yükünü providate Için [ICorProfilerInfo12:: EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) yöntemi tarafından kullanılır.
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
- [ICorProfilerInfo12:: EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md)
