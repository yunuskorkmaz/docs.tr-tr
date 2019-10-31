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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085129"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue Yöntemi
Sıfır veya null başlangıç değeri ile belirtilen türde bir değer oluşturur.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) kullanın.  
  
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
 'ndaki Değerin türünü belirten [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) numaralandırması değeri.  
  
 `pElementClass`  
 'ndaki Tür temel bir tür değilse, değerin sınıfını belirten [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) nesnesine yönelik işaretçi.  
  
 `ppValue`  
 dışı Değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValue`, tek bir işlev değerlendirmesinde kullanmak amacıyla verilen türde bir `ICorDebugValue` nesnesi oluşturur. Bu değer nesnesi, Kullanıcı sabitlerini parametre olarak geçirmek için kullanılabilir.  
  
 Değerin türü temel bir tür ise, ilk değeri sıfır veya null olur. Temel bir türün değerini ayarlamak için [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) kullanın.  
  
 `elementType` değeri ELEMENT_TYPE_CLASS ise, null nesne başvurusunu temsil eden bir "ICorDebugReferenceValue" (`ppValue`olarak döndürülen) alırsınız. Bu nesneyi, nesne başvuru parametrelerine sahip bir işlev değerlendirmesine null geçirmek için kullanabilirsiniz. `ICorDebugValue` her şeyi ayarlayamazsınız; her zaman null kalmaya devam eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateValueForType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [Icorıncertificate Geval arabirimi](icordebugeval-interface.md)
