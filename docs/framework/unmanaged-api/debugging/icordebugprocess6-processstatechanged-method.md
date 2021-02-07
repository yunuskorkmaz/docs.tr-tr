---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugProcess6::P rocessStateChanged yöntemi'
title: ICorDebugProcess6::ProcessStateChanged Yöntemi
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 8060c29598adf5d4bbe7bffb4cd6611ee19a2669
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691373"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged Yöntemi

İşlemin çalıştığını [ICorDebug](icordebug-interface.md) öğesine bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
