---
title: ICorDebugType::GetType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418724"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType Metodu
Ortak dil çalışma zamanı (CLR) yerel türünü tanımlayan bir CorElementType değeri alır <xref:System.Type> bu Icordebugtype tarafından temsil edilen.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ty`  
 [out] Değerini gösteren bir işaretçi `CorElementType` CLR belirten numaralandırma <xref:System.Type> bu `ICorDebugType` temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `ty` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) yöntemi için genel bir tür dizilerine türünü almak için çağrılabilir; Aksi takdirde çağırmayın `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
