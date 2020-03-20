---
title: VariableLocationType Sabit Listesi
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178358"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType Sabit Listesi
Bir değişkenin yerel konum türünü gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`VLT_REGISTER`|Değişken bir kayıtta.|  
|`VLT_REGISTER_RELATIVE`|Değişken, kayıt bağıyla göreli bellek konumundadır.|  
|`VLT_INVALID`|Değişken bir kayıt ta veya bir kayıt göreli bellek konumunda depolanmaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırmanın `VariableLocationType` bir üyesi [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) yöntemi ile döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
