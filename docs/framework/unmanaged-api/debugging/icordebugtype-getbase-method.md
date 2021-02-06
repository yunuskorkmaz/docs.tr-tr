---
description: ': ICorDebugType:: GetBase yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 78cd540974b540b704e946f6c723214d72e89ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658392"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase Yöntemi

Bir ICorDebugType öğesine, varsa, bu tür tarafından temsil edilen türün temel türünü temsil eden bir arabirim işaretçisi alır `ICorDebugType` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pBase`  
 dışı `ICorDebugType` Temel türü temsil eden nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir türün temel türünü aramak, bir nesnenin veya onun üst sınıflarının tüm alanlarını yazdırmak gibi yaygın hata ayıklayıcı işlevselliği uygulamak için yararlıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
