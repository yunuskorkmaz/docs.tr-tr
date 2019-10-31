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
ms.openlocfilehash: 57a82e4ec106fead105cc7f200e7e56026004328
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122375"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters Yöntemi
Bu ICorDebugType tarafından başvurulan sınıfın <xref:System.Type> parametrelerini içeren bir ICorDebugTypeEnum için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 dışı Türün parametrelerini içeren `ICorDebugTypeEnum` adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri element_type_class, element_type_valuetype, element_type_array, element_type_szarray, element_type_byref, ELEMENT_TYPE_PTR veya ELEMENT_TYPE_FNPTR ise `EnumerateTypeParameters` kullanabilirsiniz. Parametrelerin sayısı ve sırası türüne bağlıdır:  
  
- ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır. Örneğin, tür `class Dict<String,int32>`ise `EnumerateTypeParameters`, `String` ve `int32` sırayla temsil eden nesneleri içeren bir `ICorDebugTypeEnum` döndürür.  
  
- ELEMENT_TYPE_FNPTR: `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, işlev tarafından kabul edilen bağımsız değişkenlerin sayısından bir büyük olacaktır. `ICorDebugTypeEnum` yer alan ilk tür parametresi, işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek. Örneğin, türü `int32[]`gibi bir dizi türü ise`EnumerateTypeParameters`, `int32`temsil eden bir nesne içeren bir `ICorDebugTypeEnum` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
