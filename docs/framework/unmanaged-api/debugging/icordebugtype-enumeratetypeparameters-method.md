---
title: "ICorDebugType::EnumerateTypeParameters Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4b864b2b5fd4f2a6ed03218ce6e7b6f3bf62202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters Yöntemi
Arabirim işaretçisi içeren bir Icordebugtypeenum alır <xref:System.Type> bu Icordebugtype tarafından başvurulan sınıfının parametreleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 [out] Adresine bir işaretçi bir `ICorDebugTypeEnum` türünün parametrelerini içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `EnumerateTypeParameters` CorElementType değeri tarafından döndürülürse [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) olan ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_ PTR veya ELEMENT_TYPE_FNPTR. Parametreler ve bunların sırası sayısı türüne bağlıdır:  
  
-   ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: içinde yer alan türü parametre sayısı `ICorDebugTypeEnum` bu yöntem döndürdüğünü, karşılık gelen sınıf için biçimsel türündeki parametrelerin sayısı bağlı. Örneğin, tür ise `class Dict<String,int32>`, sonra `EnumerateTypeParameters` döndürür bir `ICorDebugTypeEnum` temsil eden nesneleri içeren `String` ve `int32` dizisindeki.  
  
-   ELEMENT_TYPE_FNPTR: Tür parametreleri içinde yer alan sayısını `ICorDebugTypeEnum` bir işlev tarafından kabul bağımsız değişken sayısı büyük olacaktır. İçinde yer alan ilk tür parametresi `ICorDebugTypeEnum` işlevi için dönüş türü ve sonraki tür parametreleri işlevin parametreleridir.  
  
-   ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek. Örneğin, bir dizi türü gibi türündeyse `int32[]`,`EnumerateTypeParameters` döndürülecek bir `ICorDebugTypeEnum` içeren bir nesneyi temsil eden `int32`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
