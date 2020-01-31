---
title: ICorDebugEval2::CreateValueForType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793479"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType Yöntemi
Belirtilen türdeki yeni bir ICorDebugValue değeri, sıfır veya null değeri olan bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pType`  
 'ndaki Türü temsil eden ICorDebugType nesnesine yönelik işaretçi.  
  
 `ppValue`  
 dışı Değeri temsil eden bir `ICorDebugValue` nesnesinin adresine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValueForType`, `List<int>`gibi oluşturulmuş türler de dahil olmak üzere, rastgele bir nesne türü belirtmenize izin vererek [ıcorınkıt Geval:: CreateValue](icordebugeval-createvalue-method.md) öğesini genelleştirir. Bu yöntemin tek amacı, bir işlev değerlendirmesine geçirilebilecek bir değer üretmesidir.  
  
 Tür bir sınıf veya değer türü olmalıdır. Dizi değerleri veya dize değerleri oluşturmak için bu yöntemi kullanamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
