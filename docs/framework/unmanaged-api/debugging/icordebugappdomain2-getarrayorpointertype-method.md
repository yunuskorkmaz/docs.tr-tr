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
ms.openlocfilehash: bbf43f3936823b9a8e562cb32cfa2eef08840033
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895182"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.  
  
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
 'ndaki Oluşturulacak temel yerel türü (bir dizi, işaretçi veya başvuru) belirten CorElementType numaralandırması değeri.  
  
 `nRank`  
 'ndaki Dizinin derece (yani boyut sayısı). Bir işaretçi veya başvuru türü `elementType` belirtiyorsa bu değer 0 olmalıdır.  
  
 `pTypeArg`  
 'ndaki Oluşturulacak dizi, işaretçi veya başvurunun türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.  
  
 `ppType`  
 dışı Oluşturulan diziyi, işaretçi türünü veya başvuru `ICorDebugType` türünü temsil eden nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 *ElementType* değeri aşağıdakilerden biri olmalıdır:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY  
  
 *ElementType* değeri ELEMENT_TYPE_PTR veya element_type_byref, *nRank* sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
