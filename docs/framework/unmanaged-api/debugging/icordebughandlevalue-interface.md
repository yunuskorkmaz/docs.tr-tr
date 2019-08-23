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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915002"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Arabirimi

Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Arabirim işaretçisini açıkça serbest bırakmadan bu `ICorDebugHandleValue` nesne tarafından başvurulan tanıtıcıyı serbest bırakır.|  
|[GetHandleType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Bunun `ICorDebugHandleValue`başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugReferenceValue` nesne, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır. , Açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu korur.`ICorDebugHandleValue`  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
