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
ms.openlocfilehash: ba138e79e0d6fb6f9c5e9c3efe3466f3c88cccae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782616"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame Arabirimi

Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](icordebugframe-createstepper-method.md)|Bu `ICorDebugFrame`göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır.|  
|[GetCallee Yöntemi](icordebugframe-getcallee-method.md)|Geçerli zincirde bu karenin çağırdığı `ICorDebugFrame` bir işaretçi alır veya bu, zincirdeki en içteki çerçevese null değerini döndürür.|  
|[GetCaller Yöntemi](icordebugframe-getcaller-method.md)|Bu çerçeveyi çağıran geçerli zincirde `ICorDebugFrame` bir işaretçi alır ya da zincirde en dıştaki çerçevese null değerini döndürür.|  
|[GetChain Yöntemi](icordebugframe-getchain-method.md)|Bu `ICorDebugFrame` bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır.|  
|[GetCode Yöntemi](icordebugframe-getcode-method.md)|Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.|  
|[GetFunction Yöntemi](icordebugframe-getfunction-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.|  
|[GetStackRange Yöntemi](icordebugframe-getstackrange-method.md)|Bu `ICorDebugFrame`temsil eden yığın çerçevesinin mutlak adres aralığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
