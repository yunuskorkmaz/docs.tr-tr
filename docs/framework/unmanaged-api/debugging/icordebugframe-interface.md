---
title: Icordebugframe Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a>Icordebugframe Interface1
Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Bu göreli sürüm işlemlerini gerçekleştirmek için bir ICorDebugStepper alır `ICorDebugFrame`.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Bir işaretçi alır `ICorDebugFrame` bu çerçeve olarak adlandırılan veya bu döndürür null ise zincirde en içteki çerçeve geçerli zincirindeki.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Bir işaretçi alır `ICorDebugFrame` geçerli zincirde bu çerçeve denilen ya da bu döndürür null ise zincirde en dıştaki çerçeve.|  
|[GetChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Icordebugchain gösteren bir işaretçi bu alır `ICorDebugFrame` bir parçasıdır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Bu yığın çerçevesi ile ilişkili Icordebugcode için bir işaretçi alır.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Bu yığın çerçevesi ile ilişkili kodunu içerir ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesi ile ilişkili kodunu içerir işlevi için meta veri belirtecini alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Bu tarafından temsil edilen yığın çerçevesi mutlak bir adres aralığını alır `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
