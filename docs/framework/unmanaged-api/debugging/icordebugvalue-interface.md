---
description: ': ICorDebugValue arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: cae8fdef5c1c49cbabc25d3d547cb5748a9eeee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690322"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue Arabirimi

Hata ayıklanan işlemdeki bir değeri temsil eder. Değer bir okuma veya yazma değeri olabilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugvalue-createbreakpoint-method.md)|Bu yöntem şu anda uygulanmadı.|  
|[GetAddress Yöntemi](icordebugvalue-getaddress-method.md)|Bu `ICorDebugValue` nesnenin, hata ayıklama sürecinde olan adresini alır.|  
|[GetSize Yöntemi](icordebugvalue-getsize-method.md)|Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue` .|  
|[GetType Yöntemi](icordebugvalue-gettype-method.md)|Bu nesnenin temel türünü alır `ICorDebugValue` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Genel olarak, bir değer nesnesinin sahipliği döndürüldüğünde geçirilir. Alıcı, nesne ile işiniz bittiğinde nesneden bir başvuruyu kaldırmaktan sorumludur.  
  
 Değerin nereden alındığına bağlı olarak, işlem sürdürülmeden sonra değer geçerli kalmayabilir. Bu nedenle, genellikle değer [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yönteminin bir çağrısında tutulmamalıdır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugValue3 Arabirimi](icordebugvalue3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
