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
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138475"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Arabirimi

Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Arabirim işaretçisini açıkça serbest bırakmadan bu `ICorDebugHandleValue` nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.|  
|[GetHandleType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Bu `ICorDebugHandleValue`başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugReferenceValue` nesnesi, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır. `ICorDebugHandleValue`, açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu tutar.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
