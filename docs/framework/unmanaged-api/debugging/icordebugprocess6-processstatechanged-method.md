---
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 006c81e0339a00aac14fb4f83f2bc140990bd546
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732586"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged Yöntemi

İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>Parametreler  

 `change`  
 'ndaki [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) numaralandırması üyesi  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, işlemin çalıştığını [ICorDebug](icordebug-interface.md) 'a bildirmek için bu yöntemi çağırır.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
