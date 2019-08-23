---
title: ICorDebugFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937001"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame Arabirimi

Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Bu `ICorDebugFrame`işleme göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Geçerli zincirde bu karenin çağırdığı `ICorDebugFrame` bir işaretçisini alır veya zincirde en içteki çerçevese null değerini döndürür.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Bu çerçeveyi çağıran geçerli zincirde `ICorDebugFrame` ' a bir işaretçi alır veya zincirde en dıştaki çerçevese null değerini döndürür.|  
|[GetChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Bir parçası `ICorDebugFrame` olan ıcordebugzincirine yönelik bir işaretçi alır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Bu `ICorDebugFrame`tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
