---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911335"
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
 Olayın türünü gösteren bir [Cordebugdebugger Geventkind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerine `pDebugEventKind`bağlı olarak, ek verilere sahip daha kesin `QueryInterface` bir hata ayıklama olay arabirimi almak için öğesini çağırabilirsiniz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
