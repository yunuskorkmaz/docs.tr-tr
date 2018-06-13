---
title: ICorDebugType::GetClass Metodu
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
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422568"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass Metodu
Arabirim işaretçisi dizilerine genel türünü temsil eden bir Icordebugclass alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppClass`  
 [out] Adresine bir işaretçi bir `ICorDebugClass` dizilerine genel tür temsil eden arabirim.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClass` yalnızca belirli koşullar altında çağrılabilir. Çağrı [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırmadan önce `GetClass`. Varsa `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, CorElementType değeri döndürür `GetClass` için genel bir tür dizilerine türünü almak için çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
