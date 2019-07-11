---
title: ICorDebugType::GetFirstTypeParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3031cf2d9509f94b50c386b44e6d9e5d9ee5509c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768230"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter Yöntemi
İlk temsil eden bir Icordebugtype bir arabirim işaretçisi alır <xref:System.Type> bu tarafından temsil edilen bir türün parametresinin `ICorDebugType`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `value`  
 [out] Adresine bir işaretçi bir `ICorDebugType` ilk parametre temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFirstTypeParameter` Burada türü hakkında ek bilgiler, en fazla içerir durumda bir tür parametresi çağrılabilir. Tür ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR, ise özellikle tarafından belirtildiği şekilde kullanılabilmesi için [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
