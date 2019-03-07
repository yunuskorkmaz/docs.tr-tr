---
title: ICorDebugType::GetBase Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478732"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase Yöntemi
Bu tarafından temsil edilen türü varsa temel türünü temsil eden bir Icordebugtype için bir arabirim işaretçisi alır `ICorDebugType`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBase`  
 [out] Adresine bir işaretçi bir `ICorDebugType` taban türünü temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir tür için temel tür bakarak, tüm alanları bir nesnenin ya da üst yazdırma gibi yaygın hata ayıklayıcı işlevselliği uygulamak kullanışlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
