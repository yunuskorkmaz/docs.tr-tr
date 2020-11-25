---
title: CorDebugDebugEventKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: e348e0070a5ce619f95dad9ebe4085d17f7ade6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733379"
---
# <a name="cordebugdebugeventkind-enumeration"></a>CorDebugDebugEventKind Numaralandırması

Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|Modül yükleme olayı.|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|Modül kaldırma olayı.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|Birinci şans özel durumu.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|Birinci şans Kullanıcı özel durumu.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|Bir işleyicinin bulunduğu özel durum `catch` .|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|İşlenmeyen bir özel durum.|  
  
## <a name="remarks"></a>Açıklamalar  

 `CorDebugDebugEventKind` [Icordebugdebugger gevent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) yöntemi çağırarak sabit listesinin bir üyesi döndürülür.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
