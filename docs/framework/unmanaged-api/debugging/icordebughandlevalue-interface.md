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
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794451"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Arabirimi

Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose Yöntemi](icordebughandlevalue-dispose-method.md)|Arabirim işaretçisini açıkça serbest bırakmadan bu `ICorDebugHandleValue` nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.|  
|[GetHandleType Yöntemi](icordebughandlevalue-gethandletype-method.md)|Bu `ICorDebugHandleValue`başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır.|  
  
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

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
