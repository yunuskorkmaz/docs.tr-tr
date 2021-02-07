---
description: ': ICorDebugObjectValue:: GetFieldValue metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 38dac36747b286ab16ae3310b6b59695480a6ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722197"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue Yöntemi

Bu nesne değeri için belirtilen sınıftaki belirtilen alanın değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pClass`  
 'ndaki Alan değerinin alınacağı sınıfı temsil eden bir "ICorDebugClass" nesnesine yönelik bir işaretçi.  
  
 `fieldDef`  
 'ndaki `mdFieldDef` Alanı tanımlayan meta verilere başvuruda bulunan bir belirteç.  
  
 `ppValue`  
 dışı Belirtilen alanın değerini temsil eden bir "ICorDebugValue" nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Parametresinde belirtilen sınıf, `pClass` nesne değerinin sınıfının hiyerarşisinde olmalıdır ve alan bu sınıfın bir alanı olmalıdır.  
  
 `GetFieldValue`Genel nesneler ve genel sınıflar için yöntem yine de başarılı olur. Örneğin, MyDictionary \<V> sözlükten devralırsa \<string,V> ve nesne değeri MyDictionary türünde Ise \<int32> , `ICorDebugClass` Sözlük nesnesini \<K,V> başarılı bir şekilde sözlük alanı alır \<string,int32> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
