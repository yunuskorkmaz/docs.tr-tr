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
ms.openlocfilehash: 1c45faecdb8b95af8d9e981962151c2c5d071a4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731897"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum Arabirimi

Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar. Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)|Bir özel durum nesnesinin çağrı yığını hakkında bilgi içeren, belirtilen sayıda [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesi alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugExceptionObjectCallStackEnum`Arabirim ıcorı, Genum arabirimini uygular.  
  
 `ICorDebugExceptionObjectCallStackEnum` [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi çağırarak bir örnek [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesneleriyle doldurulur. Koleksiyondaki çağrı yığını öğeleri [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md) yöntemi çağırarak Numaralandırılabilir  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
