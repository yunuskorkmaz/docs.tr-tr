---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması'
title: COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805785"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a>COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması

Bir EventPipe olayı için bir parametre türünü açıklar.
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|Parametre türü kendini açıklayan bir nesnedir.|
|`COR_PRF_EVENTPIPE_BOOLEAN`|Parametre türü bir Boole değeri.|
|`COR_PRF_EVENTPIPE_CHAR`|Parametre türü, 16 bit geniş bir karakterdir.|
|`COR_PRF_EVENTPIPE_SBYTE`|Parametre türü işaretli 8 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_BYTE`|Parametre türü işaretsiz 8 bitlik bir tamsayıdır.|
|`COR_PRF_EVENTPIPE_INT16`|Parametre türü, işaretli bir 16 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_UINT16`|Parametre türü işaretsiz 16 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_INT32`|Parametre türü işaretli bir 32 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_UINT32`|Parametre türü işaretsiz bir 32 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_INT64`|Parametre türü işaretli bir 64 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_UINT64`|Parametre türü işaretsiz bir 64 bit tamsayıdır.|
|`COR_PRF_EVENTPIPE_SINGLE`|Parametre türü 32 bitlik bir kayan noktalı sayıdır.|
|`COR_PRF_EVENTPIPE_DOUBLE`|Parametre türü 64 bitlik bir kayan noktalı sayıdır.|
|`COR_PRF_EVENTPIPE_DECIMAL`|Parametre türü 128 bitlik bir kayan noktalı sayıdır.|
|`COR_PRF_EVENTPIPE_DATETIME`|Parametre türü serileştirilmiş bir DataTime yapısıdır.|
|`COR_PRF_EVENTPIPE_GUID`|Parametre türü bir GUID 'dir.|
|`COR_PRF_EVENTPIPE_STRING`|Parametre türü, 16 bit boş sonlandırılmış geniş karakter dizesidir.|
|`COR_PRF_EVENTPIPE_ARRAY`|Parametre türü, yukarıdaki türlerden birinin bir dizisidir.|
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_EVENTPIPE_PARAM_TYPE`Sabit listesi, [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) yapısı tarafından parametrenin türünü belirtmek için kullanılır.
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
