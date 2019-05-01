---
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946217"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass Yöntemi
Örneklenmemiş genel türü temsil eden bir Icordebugclass bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppClass`  
 [out] Adresine bir işaretçi bir `ICorDebugClass` örneklenmemiş genel türü temsil eden arabirim.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClass` yalnızca belirli koşullar altında çağrılabilir. Çağrı [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırmadan önce `GetClass`. Varsa `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, bir CorElementType değeri döndürür `GetClass` örneklenmemiş türü için genel bir tür almak için çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
