---
title: ICorDebugValue::GetType Yöntemi
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
ms.openlocfilehash: 284a74823b01305f8c6e025f70bb9209c8607b7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137070"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType Yöntemi
Bu "ICorDebugValue" nesnesinin temel türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pType`  
 dışı Değerin türünü gösteren "CorElementType" sabit listesinin bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesne karmaşık bir çalışma zamanı türü ise, bu tür `ICorDebugValue` arabiriminin uygun alt sınıfları aracılığıyla incelenebilir. Örneğin, `ICorDebugValue`devralan "ICorDebugObjectValue" karmaşık bir türü temsil eder.  
  
 `GetType` ve [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür. Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
