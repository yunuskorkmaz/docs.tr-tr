---
title: ICorDebugGenericValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981991"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue Arabirimi

"Tüm değerlere uygulanır Icordebugvalue" öğesinin. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Değeri belirtilen arabelleğe kopyalar.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Yeni bir değer belirtilen arabellek kopyalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugGenericValue` erişilemeyen olduğu için alt arabirimidir.  
  
 Başvuru türleri için başvuru içeriği yerine başvuru değerdir.  
  
 Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
