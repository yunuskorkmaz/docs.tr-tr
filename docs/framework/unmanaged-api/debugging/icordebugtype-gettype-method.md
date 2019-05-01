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
ms.openlocfilehash: f6b36c524921a4fecf8bc5ddcbace62af6450b6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993908"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType Metodu
Ortak dil çalışma zamanı (CLR) yerel türünü açıklayan bir CorElementType değerini alır <xref:System.Type> bu Icordebugtype tarafından temsil edilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ty`  
 [out] Bir işaretçi değerini `CorElementType` CLR gösteren numaralandırma <xref:System.Type> bu `ICorDebugType` temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `ty` ELEMENT_TYPE_CLASS ya da ELEMENT_TYPE_VALUETYPE, [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) yöntemi örneklenmemiş türü için genel bir tür almak için çağrılabilir; Aksi takdirde, çağırmayın `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
