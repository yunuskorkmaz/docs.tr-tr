---
description: ': ICorDebugExceptionObjectCallStackEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c72f4299bf3ebc5de2d2ed196801d93ff5fe4356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693362"
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
