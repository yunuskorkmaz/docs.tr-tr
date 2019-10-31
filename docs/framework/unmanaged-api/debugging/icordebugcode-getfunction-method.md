---
title: ICorDebugCode::GetFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: 217ca0a850926e5f697340cece264c6ed442a9bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125639"
---
# <a name="icordebugcodegetfunction-method"></a>ICorDebugCode::GetFunction Yöntemi
Bu "ICorDebugCode" ile ilişkili "ICorDebugFunction" öğesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppFunction`  
 dışı İşlevin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode` ve `ICorDebugFunction` bire bir ilişki bakımını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
