---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 92606d7bd0a277dd327ce4fd430ce963a260206d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136652"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind Yöntemi
Bu `ICorDebugDebugEvent` nesnesinin ne tür bir olayın temsil ettiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 Pıbu Geventkind  
 Olayın türünü gösteren bir [Cordebugdebugger Geventkind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `pDebugEventKind`değerine bağlı olarak, ek verilere sahip daha kesin bir hata ayıklama olay arabirimi almak için `QueryInterface` çağırabilirsiniz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
