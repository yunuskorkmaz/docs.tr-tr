---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976401"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind Yöntemi
Bu `ICorDebugDebugEvent` nesnenin ne tür bir olayın temsil ettiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 Pıbu Geventkind  
 Olayın türünü gösteren bir [Cordebugdebugger Geventkind](cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerine bağlı `pDebugEventKind`olarak, ek verilere sahip daha kesin `QueryInterface` bir hata ayıklama olay arabirimi almak için öğesini çağırabilirsiniz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDebugEvent Arabirimi](icordebugdebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
