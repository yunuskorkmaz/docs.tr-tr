---
title: ICorDebugStringValue::GetLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b168673e76beddd8ae0479b8daae009c5f057b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987382"
---
# <a name="icordebugstringvaluegetlength-method"></a>ICorDebugStringValue::GetLength Yöntemi
Bu Icordebugstringvalue tarafından başvurulan dizedeki karakter sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pcchString`  
 [out] Bu tarafından başvurulan dize uzunluğunu belirten bir değer için bir işaretçi `ICorDebugStringValue` nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
