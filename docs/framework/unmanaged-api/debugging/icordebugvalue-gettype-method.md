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
ms.openlocfilehash: 06f403f0b653866428a41240f99833ec1180eb86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731091"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType Yöntemi

Bu "ICorDebugValue" nesnesinin temel türünü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pType`  
 dışı Değerin türünü gösteren "CorElementType" sabit listesinin bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Nesne karmaşık bir çalışma zamanı türü ise, bu tür arabirimin uygun alt sınıfları aracılığıyla incelenebilir `ICorDebugValue` . Örneğin, öğesinden devralan "ICorDebugObjectValue" `ICorDebugValue` karmaşık bir türü temsil eder.  
  
 `GetType`Ve [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür. Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
