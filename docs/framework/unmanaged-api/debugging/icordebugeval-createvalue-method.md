---
title: ICorDebugEval::CreateValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976258"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue Yöntemi
Sıfır veya null başlangıç değeri ile belirtilen türde bir değer oluşturur.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `elementType`  
 'ndaki Değerin türünü belirten [CorElementType](../metadata/corelementtype-enumeration.md) numaralandırması değeri.  
  
 `pElementClass`  
 'ndaki Tür temel bir tür değilse, değerin sınıfını belirten [ICorDebugClass](icordebugclass-interface.md) nesnesine yönelik işaretçi.  
  
 `ppValue`  
 dışı Değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValue`tek bir `ICorDebugValue` işlev değerlendirmesinde kullanmak amacıyla verilen türde bir nesne oluşturur. Bu değer nesnesi, Kullanıcı sabitlerini parametre olarak geçirmek için kullanılabilir.  
  
 Değerin türü temel bir tür ise, ilk değeri sıfır veya null olur. Temel bir türün değerini ayarlamak için [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) kullanın.  
  
 Değeri ELEMENT_TYPE_CLASS `elementType` ise, null nesne başvurusunu temsil eden bir "ICorDebugReferenceValue" (içinde `ppValue`döndürülen) alırsınız. Bu nesneyi, nesne başvuru parametrelerine sahip bir işlev değerlendirmesine null geçirmek için kullanabilirsiniz. Her şeye ayarlayamazsınız `ICorDebugValue` ; her zaman null kalmaya devam eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateValueForType Yöntemi](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval Arabirimi](icordebugeval-interface.md)
