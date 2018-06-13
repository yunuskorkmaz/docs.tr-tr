---
title: ICorDebugValue::GetType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc0dd03abc1adb8eeea76a1053fb4d58de4ecf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419838"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType Metodu
Bu "ICorDebugValue" nesne temel türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pType`  
 [out] Değerin türünü gösteren "CorElementType" numaralandırma değerini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesne karmaşık bir çalışma zamanı tür ise, bu tür uygun sınıfları incelenmesi `ICorDebugValue` arabirimi. "Hangi devraldığı Örneğin, Icordebugobjectvalue", `ICorDebugValue`, karmaşık bir türü temsil eder.  
  
 `GetType` Ve [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) yöntemlerinin her bir değerin türü hakkında bilgi döndürür. Bunların her ikisi de genel türler algılayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
