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
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209636"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame Arabirimi

Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](icordebugframe-createstepper-method.md)|Bu işleme göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame` .|  
|[GetCallee Yöntemi](icordebugframe-getcallee-method.md)|`ICorDebugFrame`Geçerli zincirde bu karenin çağırdığı bir işaretçisini alır veya zincirde en içteki çerçevese null değerini döndürür.|  
|[GetCaller Yöntemi](icordebugframe-getcaller-method.md)|`ICorDebugFrame`Bu çerçeveyi çağıran geçerli zincirde ' a bir işaretçi alır veya zincirde en dıştaki çerçevese null değerini döndürür.|  
|[GetChain Yöntemi](icordebugframe-getchain-method.md)|Bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır `ICorDebugFrame` .|  
|[GetCode Yöntemi](icordebugframe-getcode-method.md)|Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.|  
|[GetFunction Yöntemi](icordebugframe-getfunction-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.|  
|[GetStackRange Yöntemi](icordebugframe-getstackrange-method.md)|Bu tarafından temsil edilen yığın çerçevesinin mutlak adres aralığını alır `ICorDebugFrame` .|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
