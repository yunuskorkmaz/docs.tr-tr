---
title: ICorDebugAppDomain2::GetArrayOrPointerType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c08a56ff7f6bd109c5568a7f992850708a22a4b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType Metodu
Belirtilen türe veya bir işaretçi veya belirtilen tür referansı dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Temel alınan yerel tür (bir dizi, işaretçi veya başvuru) oluşturulacak belirtir CorElementType numaralandırması değeri.  
  
 `nRank`  
 [in] Derecesini (diğer bir deyişle, Boyutlar sayısı) dizisi. Bu değer 0 olmalıdır `elementType` bir işaretçi veya başvuru türünü belirtir.  
  
 `pTypeArg`  
 [in] İşaretçi Icordebugtype nesneye dizi türünü temsil eder, işaretçi veya başvuru oluşturulacak.  
  
 `ppType`  
 [out] Adresine bir işaretçi bir `ICorDebugType` oluşturulan dizi, işaretçi türü veya reference temsil eden nesne türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Değeri *elementType* şunlardan biri olmalıdır:  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY  
  
 Varsa değerini *elementType* ELEMENT_TYPE_PTR veya ELEMENT_TYPE_BYREF, *nRank* sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
