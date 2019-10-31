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
ms.openlocfilehash: 861d5daa481132d3d6527e8d5fbccfab6436c5fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139113"
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
|`VLT_REGISTER`|Değişken bir yazmaç içinde.|  
|`VLT_REGISTER_RELATIVE`|Değişken, YAZMAÇ göreli bir bellek konumudur.|  
|`VLT_INVALID`|Değişken, YAZMAÇ veya yazmaç göreli bellek konumunda depolanmaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VariableLocationType` numaralandırmanın bir üyesi [ıcordebugvariablehome:: GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
