---
title: CorDebugDecodeEventFlagsWindows Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: da3a100bd552eaa3233642b006e0265adbcac1ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132208"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>CorDebugDecodeEventFlagsWindows Numaralandırması
Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|Hata ayıklama olayının ilk şans özel durumu olduğunu gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugProcess6::D ecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi, bir hata ayıklama olayı ve değeri hedef mimarisine bağlı olan ek bilgiler sağlayan bir `dwFlags` parametresi içerir. `CorDebugDecodeEventFlagsWindows` numaralandırması, Windows platformunda hata ayıklama olayları ile kullanılabilir.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
