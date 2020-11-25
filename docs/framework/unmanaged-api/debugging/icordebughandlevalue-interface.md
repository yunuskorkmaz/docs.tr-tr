---
title: ICorDebugHandleValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: e695a93036e00e651ecababb0e1407661bcc48d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729089"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Arabirimi

Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose yöntemi](icordebughandlevalue-dispose-method.md)|`ICorDebugHandleValue`Arabirim işaretçisini açıkça serbest bırakmadan bu nesne tarafından başvurulan tanıtıcıyı serbest bırakır.|  
|[GetHandleType Yöntemi](icordebughandlevalue-gethandletype-method.md)|Bunun başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır `ICorDebugHandleValue` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `ICorDebugReferenceValue` nesne, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır. `ICorDebugHandleValue`, Açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu korur.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
