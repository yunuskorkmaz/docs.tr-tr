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
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791150"
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
  
 `GetType` ve [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür. Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
