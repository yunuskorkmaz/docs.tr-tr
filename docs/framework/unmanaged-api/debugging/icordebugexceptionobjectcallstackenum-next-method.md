---
title: ICorDebugExceptionObjectCallStackEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 38de810509f15cf93475eb000837892b99684fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782744"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugExceptionObjectCallStackEnum::Next Yöntemi
Özel durum nesnesinin çağrı yığınından bilgi içeren, belirtilen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısı.  
  
 `values`  
 dışı Her biri [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesine işaret eden bir işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Gerçekte döndürülen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionObjectCallStackEnum Arabirimi](icordebugexceptionobjectcallstackenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
