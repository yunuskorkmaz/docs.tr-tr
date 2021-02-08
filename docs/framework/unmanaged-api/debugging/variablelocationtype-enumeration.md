---
description: 'Daha fazla bilgi edinin: VariableLocationType numaralandırması'
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
ms.openlocfilehash: 8561077b9f3f4d318eeb743d51538b2a9a22a217
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800532"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType Sabit Listesi

Bir değişkenin yerel konum türünü gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`VLT_REGISTER`|Değişken bir yazmaç içinde.|  
|`VLT_REGISTER_RELATIVE`|Değişken, YAZMAÇ göreli bir bellek konumudur.|  
|`VLT_INVALID`|Değişken, YAZMAÇ veya yazmaç göreli bellek konumunda depolanmaz.|  
  
## <a name="remarks"></a>Açıklamalar  

 Sabit listesinin bir üyesi `VariableLocationType` [ıcordebugvariablehome:: GetLocationType](icordebugvariablehome-getlocationtype-method.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
