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
ms.openlocfilehash: b4d2ba850ffc6e49cf330174dda9524c7bac4549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709201"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType Metodu
Bu "ICorDebugValue" nesnenin temel türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pType`  
 [out] "CorElementType" numaralandırma değerinin türü belirten bir değer için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Uygun adornerset'in alt nesne karmaşık bir çalışma zamanı tür ise, bu tür incelenmesi `ICorDebugValue` arabirimi. "Öğesinden devralan gibi Icordebugobjectvalue", `ICorDebugValue`, karmaşık bir türü temsil eder.  
  
 `GetType` Ve [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) yöntemlerinin her bir değer türü hakkında bilgi döndürür. Bunların her ikisi de genel türleri tanımayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

