---
description: 'Daha fazla bilgi edinin: ICorDebugValue2:: GetExactType yöntemi'
title: ICorDebugValue2::GetExactType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690316"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType Yöntemi

Bu değerin değerini temsil eden bir "ICorDebugType" nesnesine bir arabirim işaretçisi alır <xref:System.Type> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppType`  
 dışı `ICorDebugType` <xref:System.Type> Bu "ICorDebugValue2" nesnesinin temsil ettiği değeri temsil eden nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Genel türler kullanan `GetExactType` Yöntem hem [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) hem de [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemlerinin yerine, her biri bir değer türü ile ilgili bilgileri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
