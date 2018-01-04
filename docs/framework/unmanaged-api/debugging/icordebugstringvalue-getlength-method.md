---
title: ICorDebugStringValue::GetLength Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue.GetLength
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 129998bc2e7530aefefb2655a83cb04a9aa4cc6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvaluegetlength-method"></a>ICorDebugStringValue::GetLength Metodu
Bu Icordebugstringvalue tarafından başvurulan dizedeki karakter sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcchString`  
 [out] Bu tarafından başvurulan dize uzunluğu belirten bir değer için bir işaretçi `ICorDebugStringValue` nesnesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
