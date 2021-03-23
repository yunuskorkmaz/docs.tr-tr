---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması'
title: COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_DESC
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: b23897580092cc9f3f887a21e86f7111fecd9f19
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805798"
---
# <a name="cor_prf_eventpipe_param_desc-enumeration"></a>COR_PRF_EVENTPIPE_PARAM_DESC numaralandırması

Bir EventPipe olayının parametre adını ve türünü açıklar.
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct
{
    UINT32       type;
    UINT32       elementType;
    const WCHAR *name;
} COR_PRF_EVENTPIPE_PARAM_DESC;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`type`|Parametrenin türü.|  
|`elementType`|Bu parametre bir dizi türü ise öğe türü.|  
|`name`|Parametrenin adını içeren geniş bir karakter dizesi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_EVENTPIPE_PARAM_DESC`Yapı, tanımlanmakta olan olayın parametre türlerini tanımlamak Için [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) yöntemi tarafından kullanılır.
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
- [ICorProfilerInfo12:: EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md)
