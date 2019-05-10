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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b48e375286e709a2ce570769c9a0453765824ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622682"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters Yöntemi
Bir arabirim işaretçisi alır içeren bir Icordebugtypeenum <xref:System.Type> bu Icordebugtype tarafından başvurulan sınıfın parametreleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 [out] Adresine bir işaretçi bir `ICorDebugTypeEnum` tür parametreleri içeren.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `EnumerateTypeParameters` CorElementType değeri tarafından döndürdüyse [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ve ELEMENT_TYPE_ PTR veya ELEMENT_TYPE_FNPTR. Parametreler ve bunların sırası sayısını türüne bağlıdır:  
  
- ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: Bulunan tür parametreleri sayısı `ICorDebugTypeEnum` bu yöntem döndürdüğünü, karşılık gelen sınıf için biçimsel tür parametrelerinin sayısına bağımlı. Örneğin, türü ise `class Dict<String,int32>`, ardından `EnumerateTypeParameters` döndürür bir `ICorDebugTypeEnum` temsil eden nesneler içeren `String` ve `int32` dizideki.  
  
- ELEMENT_TYPE_FNPTR: Bulunan tür parametreleri sayısı `ICorDebugTypeEnum` bir bağımsız değişken işlev tarafından kabul sayısından daha büyük olacaktır. Bulunan ilk tür parametresi `ICorDebugTypeEnum` işlevin dönüş türü ve sonraki tür parametreleri, işlevin parametrelerdir.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: Bir tür parametresi döndürülür. Örneğin, türü gibi bir dizi türü ise `int32[]`,`EnumerateTypeParameters` döndüreceği bir `ICorDebugTypeEnum` içeren bir nesneyi temsil eden `int32`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
