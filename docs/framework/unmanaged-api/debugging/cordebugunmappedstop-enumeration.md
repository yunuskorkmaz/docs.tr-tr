---
title: CorDebugUnmappedStop Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132742"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop Numaralandırması
Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`STOP_NONE`|Herhangi bir eşlenmemiş kod türünde durmayın.|  
|`STOP_PROLOG`|Giriş kodunda durdur.|  
|`STOP_EPILOG`|Bitiş kodunda durdur.|  
|`STOP_NO_MAPPING_INFO`|Eşleme bilgilerine sahip olmayan kodda durdur.|  
|`STOP_OTHER_UNMAPPED`|Giriş, bitiş, hiçbir eşleme bilgisi veya yönetilmeyen kategoriye uymayan eşlenmemiş kodda durun.|  
|`STOP_UNMANAGED`|Yönetilmeyen kodda durdur. Bu değer yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.|  
|`STOP_ALL`|Eşlenmemiş kod türlerinde durun.|  
  
## <a name="remarks"></a>Açıklamalar  
 Stepper 'in durdurulacağı eşlenmemiş kodu belirten bayrakları ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
