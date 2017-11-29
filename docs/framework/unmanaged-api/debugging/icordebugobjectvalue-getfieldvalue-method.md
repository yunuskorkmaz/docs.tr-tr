---
title: ICorDebugObjectValue::GetFieldValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33c3f368d9b78b899f54c989427ea1f660346487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue Metodu
Bu nesne değeri için belirtilen sınıf belirtilen alanının değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Bir işaretçi "ICorDebugClass" nesneye için alan değeri almak istediğiniz sınıfı temsil eder.  
  
 `fieldDef`  
 [in] Bir `mdFieldDef` alan açıklayan meta veriler başvuran belirteci.  
  
 `ppValue`  
 [out] Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesnesi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen sınıf `pClass` parametresi, nesne değerinin sınıfının hiyerarşisinde olmalıdır ve alan bu sınıfın bir alan olmalıdır.  
  
 `GetFieldValue` Yöntemi yine de başarılı genel nesneler ve Genel sınıflar için. Örneğin, varsa MyDictionary\<V > sözlükten devralır\<dize, V >, ve nesne değeri türü MyDictionary\<Int32 >, geçen `ICorDebugClass` sözlük nesnesi\<K, V > olur başarıyla sözlük alanı almak\<dize, Int32 >.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
 
