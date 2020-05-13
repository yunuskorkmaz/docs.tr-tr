---
title: ICorDebugType::EnumerateTypeParameters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380000"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters Yöntemi
<xref:System.Type>Bu ICorDebugType tarafından başvurulan sınıfın parametrelerini Içeren ICorDebugTypeEnum için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 dışı `ICorDebugTypeEnum`Türünün parametrelerini içeren adresinin bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateTypeParameters` [ICorDebugType:: GetType](icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri element_type_class, element_type_valuetype, element_type_array, element_type_szarray, element_type_byref, ELEMENT_TYPE_PTR veya element_type_fnptr ise kullanabilirsiniz. Parametrelerin sayısı ve sırası türüne bağlıdır:  
  
- ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü ' de bulunan tür parametrelerinin sayısı `ICorDebugTypeEnum` , karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır. Örneğin, türü ise `class Dict<String,int32>` , `EnumerateTypeParameters` `ICorDebugTypeEnum` ve sırasını temsil eden nesneleri içeren bir döndürür `String` `int32` .  
  
- ELEMENT_TYPE_FNPTR: içinde yer alan tür parametrelerinin sayısı, `ICorDebugTypeEnum` işlev tarafından kabul edilen bağımsız değişken sayısından bir büyük olacaktır. İçinde yer alan ilk tür parametresi, `ICorDebugTypeEnum` işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek. Örneğin, türü gibi bir dizi türü ise `int32[]` , `EnumerateTypeParameters` `ICorDebugTypeEnum` temsil eden nesneyi içeren bir nesnesi döndürür `int32` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
