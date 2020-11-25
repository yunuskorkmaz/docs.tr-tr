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
ms.openlocfilehash: cfa0950ca2ef4e969258c147b762fa95e52a82e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705828"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue Arabirimi

Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetValue Metodu](icordebuggenericvalue-getvalue-method.md)|Değeri belirtilen arabelleğe kopyalar.|  
|[SetValue Yöntemi](icordebuggenericvalue-setvalue-method.md)|Belirtilen arabellekteki yeni bir değer kopyalar.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugGenericValue` , Uzaktan erişilemeyen için bir alt arabirimdir.  
  
 Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.  
  
 Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
