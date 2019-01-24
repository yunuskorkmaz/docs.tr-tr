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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f22c045be9af71644415ae3b6b5e64d3e399dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495441"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop Numaralandırması
Kod yürütülmesine bir durdurmak tarafından adımlayıcıdaki tetikleyebilirsiniz eşlenmemiş kodun türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`STOP_NONE`|Herhangi bir türde eşlenmemiş kod durdurmayın.|  
|`STOP_PROLOG`|Giriş kodu durdurun.|  
|`STOP_EPILOG`|Sonuç kodu durdurun.|  
|`STOP_NO_MAPPING_INFO`|Eşleme bilgisi kodda durdurun.|  
|`STOP_OTHER_UNMAPPED`|Giriş, bitiş, Hayır eşleme bilgilerini veya yönetilmeyen bir kategori uymayan eşlenmemiş kodda durdurun.|  
|`STOP_UNMANAGED`|Yönetilmeyen kodda durdurun. Bu değer, yalnızca birlikte çalışma hata ayıklama ile geçerlidir.|  
|`STOP_ALL`|Eşlenmemiş kod tüm türlerin durdurun.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlayıcı durdurur eşlenmemiş kod belirten bayrakları ayarlamanızı yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
