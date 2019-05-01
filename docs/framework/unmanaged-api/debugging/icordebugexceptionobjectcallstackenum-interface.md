---
title: ICorDebugExceptionObjectCallStackEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ed6c04a46a767ed122e54df0695429cf923b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988916"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum Arabirimi
Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar. Icordebugenum arabirimi öğesinin arabirimidir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Icordebugexceptionobjectcallstackenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|Belirtilen sayıda alır [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) bir özel durum nesnenin çağrı yığını hakkında bilgi içeren nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugExceptionObjectCallStackEnum` Arabirimi uygulayan Icordebugenum arabirimi.  
  
 Bir `ICorDebugExceptionObjectCallStackEnum` örneği ile doldurulur [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) çağırarak nesneleri [Icordebugexceptionobjectvalue::enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi. Çağrı yığını öğeleri koleksiyonu çağırarak numaralandırılabilir [Icordebugexceptionobjectcallstackenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) yöntemi  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
