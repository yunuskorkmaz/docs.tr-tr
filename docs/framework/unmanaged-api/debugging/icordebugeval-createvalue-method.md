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
ms.openlocfilehash: 41db6ac00d8646651d0e8433d076c37af6020071
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696160"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue Yöntemi

Sıfır veya null başlangıç değeri ile belirtilen türde bir değer oluşturur.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 `CreateValue``ICorDebugValue`tek bir işlev değerlendirmesinde kullanmak amacıyla verilen türde bir nesne oluşturur. Bu değer nesnesi, Kullanıcı sabitlerini parametre olarak geçirmek için kullanılabilir.  
  
 Değerin türü temel bir tür ise, ilk değeri sıfır veya null olur. Temel bir türün değerini ayarlamak için [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) kullanın.  
  
 Değeri `elementType` element_type_class ise, `ppValue` null nesne başvurusunu temsil eden bir "ICorDebugReferenceValue" (içinde döndürülen) alırsınız. Bu nesneyi, nesne başvuru parametrelerine sahip bir işlev değerlendirmesine null geçirmek için kullanabilirsiniz. `ICorDebugValue`Her şeyi hiçbir şekilde ayarlayamazsınız; her zaman null kalır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateValueForType Yöntemi](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval Arabirimi](icordebugeval-interface.md)
