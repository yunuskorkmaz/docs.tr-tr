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
ms.openlocfilehash: f77708a5b315cb65b54ffa0983caa17176d01324
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974477"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame Arabirimi

Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Bu göreli Adımlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Bir işaretçi alır `ICorDebugFrame` bu çerçeve adlı veya bu null döndürür zincirindeki en içteki çerçeve olan geçerli zincirindeki.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Bir işaretçi alır `ICorDebugFrame` geçerli zincirinde bu çerçeve adında ya da bu null döndürür zincirindeki en dıştaki çerçeve.|  
|[GetChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Bu Icordebugchain bir işaretçi alır `ICorDebugFrame` bir parçasıdır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Bu yığın çerçevesiyle ilgili Icordebugcode için bir işaretçi alır.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Bu yığın çerçevesiyle ilgili kodu içeren ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesiyle ilgili kodu içeren işlevi için meta veri belirteci alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
