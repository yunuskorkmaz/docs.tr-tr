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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791307"
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
 [ICorDebugType:: GetType](icordebugtype-gettype-method.md) tarafından döndürülen CorElementType değeri ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR veya ELEMENT_TYPE_FNPTR ise `EnumerateTypeParameters` kullanabilirsiniz. Parametrelerin sayısı ve sırası türüne bağlıdır:  
  
- ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bu yöntemin döndürdüğü `ICorDebugTypeEnum` içerilen tür parametrelerinin sayısı, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağlıdır. Örneğin, tür `class Dict<String,int32>`ise `EnumerateTypeParameters`, `String` ve `int32` sırayla temsil eden nesneleri içeren bir `ICorDebugTypeEnum` döndürür.  
  
- ELEMENT_TYPE_FNPTR: `ICorDebugTypeEnum` içindeki tür parametrelerinin sayısı, işlev tarafından kabul edilen bağımsız değişken sayısından bir daha büyük olacaktır. `ICorDebugTypeEnum` yer alan ilk tür parametresi, işlevin dönüş türüdür ve sonraki tür parametreleri işlevin parametreleridir.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek. Örneğin, türü `int32[]`gibi bir dizi türü ise`EnumerateTypeParameters`, `int32`temsil eden bir nesne içeren bir `ICorDebugTypeEnum` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
