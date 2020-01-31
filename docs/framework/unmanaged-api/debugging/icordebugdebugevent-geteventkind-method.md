---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783407"
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
 Olayın türünü gösteren bir [Cordebugdebugger Geventkind](cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.  
  
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

- [ICorDebugDebugEvent Arabirimi](icordebugdebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
