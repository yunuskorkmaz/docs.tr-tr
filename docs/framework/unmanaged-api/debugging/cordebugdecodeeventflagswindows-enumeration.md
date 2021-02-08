---
description: 'Daha fazla bilgi edinin: CorDebugDecodeEventFlagsWindows sabit listesi'
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
ms.openlocfilehash: 765ce4b967d00bd70becca666e2ed418614d6fe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801702"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>CorDebugDecodeEventFlagsWindows Numaralandırması

Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|Hata ayıklama olayının ilk şans özel durumu olduğunu gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICorDebugProcess6::D ecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi `dwFlags` bir hata ayıklama olayı ve değeri hedef mimarisine bağlı olan ek bilgiler sağlayan bir parametre içerir. `CorDebugDecodeEventFlagsWindows`Sabit listesi Windows platformunda hata ayıklama olayları ile kullanılabilir.  
  
> [!NOTE]
> Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
