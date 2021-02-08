---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugMappingResult numaralandırması'
title: CorDebugMappingResult Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 03454e2fbfa8fabca89805ea51a6cfba27aa792f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801598"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult Numaralandırması

Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Yerel kod giriş durumunda olduğundan IP değeri 0 ' dır.|  
|`MAPPING_EPILOG`|Yerel kod bir bitişdir, bu nedenle IP değeri yöntemin son yönergesinin adresidir.|  
|`MAPPING_NO_INFO`|Yöntemi için hiçbir eşleme bilgisi yok, bu nedenle IP değeri 0 ' dır.|  
|`MAPPING_UNMAPPED_ADDRESS`|Yöntemi için eşleme bilgileri olsa da, geçerli adres Microsoft ara dili (MSIL) koduna eşlenemez. IP değeri 0 ' dır.|  
|`MAPPING_EXACT`|Yöntemi tamamen MSIL koduna eşlenir veya çerçeve yorumlanmış olduğundan, IP değeri doğru olmalıdır.|  
|`MAPPING_APPROXIMATE`|Yöntem başarıyla eşlendi, ancak IP 'nin değeri yaklaşık olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Yönerge işaretçisinin değerini elde etmek için [ICorDebugILFrame:: GetIP](icordebugilframe-getip-method.md) yöntemini kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
