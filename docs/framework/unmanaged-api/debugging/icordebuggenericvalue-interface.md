---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugGenericValue arabirimi'
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
ms.openlocfilehash: 7c81855849d7b72bc509d20072b96bb64f5d395a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692043"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue Arabirimi

Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetValue Yöntemi](icordebuggenericvalue-getvalue-method.md)|Değeri belirtilen arabelleğe kopyalar.|  
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
