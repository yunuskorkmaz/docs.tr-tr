---
title: ICorDebugObjectValue::GetFieldValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994571"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue Yöntemi
Bu nesne değeri için belirtilen sınıf belirtilen alanının değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Alan değeri alınacağı bir sınıfı temsil eden bir "ICorDebugClass" nesne işaretçisi.  
  
 `fieldDef`  
 [in] Bir `mdFieldDef` başvuran alanı tanımlayan meta veri belirteci.  
  
 `ppValue`  
 [out] Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesne işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen sınıfın `pClass` parametresi, nesne değerinin sınıfının hiyerarşisinde olmalıdır ve söz konusu sınıfın bir alan alan olmalıdır.  
  
 `GetFieldValue` Yöntemi yine de başarılı olur genel nesneleri ve Genel sınıflar için. Örneğin, varsa MyDictionary\<V > sözlükten devralan\<dize, V >, ve nesne değeri MyDictionary türünde\<Int32 >, geçen `ICorDebugClass` sözlük nesnesi\<K, V > olur sözlüğün bir alan başarıyla alma\<string, Int32 >.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
