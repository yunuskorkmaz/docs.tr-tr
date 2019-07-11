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
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772039"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase Yöntemi
Bu tarafından temsil edilen türü varsa temel türünü temsil eden bir Icordebugtype için bir arabirim işaretçisi alır `ICorDebugType`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
