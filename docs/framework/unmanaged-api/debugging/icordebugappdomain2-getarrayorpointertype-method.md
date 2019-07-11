---
title: ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd8f71ca75a795ab86c61140eacbbcfb0a18b590
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737808"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
Belirtilen tür veya işaretçi veya başvuru belirtilen türe dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Temel alınan yerel tür (bir dizi, işaretçi veya başvuru) oluşturulacak belirtir CorElementType sabit listesi değeri.  
  
 `nRank`  
 [in] Boyut (diğer bir deyişle, boyut sayısı) dizisi. Bu değer, 0 olmalıdır `elementType` bir işaretçi veya başvuru türü belirtir.  
  
 `pTypeArg`  
 [in] Bir dizi türünü temsil eden bir Icordebugtype nesne işaretçisi, işaretçi veya başvuru oluşturulacak.  
  
 `ppType`  
 [out] Adresine bir işaretçi bir `ICorDebugType` oluşturulmuş dizi, işaretçi türü veya başvuru temsil eden bir nesne türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerini *elementType* aşağıdakilerden biri olmalıdır:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY  
  
 Varsa değerini *elementType* ELEMENT_TYPE_PTR veya ELEMENT_TYPE_BYREF, *nRank* sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
