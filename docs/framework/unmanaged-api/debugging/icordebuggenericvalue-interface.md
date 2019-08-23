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
ms.openlocfilehash: 36c2ed5529151a7ea18ccaffc2202ad6c69bcbd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910224"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue Arabirimi

Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı. Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Değeri belirtilen arabelleğe kopyalar.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Belirtilen arabellekteki yeni bir değer kopyalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugGenericValue`, Uzaktan erişilemeyen için bir alt arabirimdir.  
  
 Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.  
  
 Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
