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
ms.openlocfilehash: 6fce9f61e222d0fc1763495de162a94a7fc22689
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975985"
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionObjectCallStackEnum Arabirimi](icordebugexceptionobjectcallstackenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
