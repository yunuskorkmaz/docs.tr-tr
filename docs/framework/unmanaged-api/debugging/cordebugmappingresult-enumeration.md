---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2042d0936359a85d203375c42be0d8a096f004e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739754"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult Numaralandırması
Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Yerel kod giriş bölümünde olduğundan IP değeri 0'dır.|  
|`MAPPING_EPILOG`|Yerel kod bir sonuç içinde olduğundan, yöntemin son yönerge adresi IP değeri.|  
|`MAPPING_NO_INFO`|IP değeri 0, bu nedenle yöntemi için hiçbir eşleme bilgisi kullanılabilir.|  
|`MAPPING_UNMAPPED_ADDRESS`|Eşleme bilgileri yöntemi olsa da, Microsoft Ara dili (MSIL) kodu için geçerli adresi eşlenemez. IP değeri 0'dır.|  
|`MAPPING_EXACT`|Yöntemin MSIL kodu tam olarak eşler ya da IP değeri doğru Bu nedenle çerçeve, algılanır.|  
|`MAPPING_APPROXIMATE`|Yöntem başarılı bir şekilde eşlendi ancak IP değeri yaklaşık olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz [Icordebugılframe::getıp](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) yönerge işaretçisini değerini elde etmek için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
