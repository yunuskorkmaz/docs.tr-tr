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
ms.openlocfilehash: e60d4b128bf03ff81863e0c95815b2c204807583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794465"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue Arabirimi

Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetValue Yöntemi](icordebuggenericvalue-getvalue-method.md)|Değeri belirtilen arabelleğe kopyalar.|  
|[SetValue Yöntemi](icordebuggenericvalue-setvalue-method.md)|Belirtilen arabellekteki yeni bir değer kopyalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugGenericValue`, Uzaktan erişilemeyen için bir alt arabirimdir.  
  
 Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.  
  
 Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
