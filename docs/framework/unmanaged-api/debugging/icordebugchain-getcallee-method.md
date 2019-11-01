---
title: ICorDebugChain::GetCallee Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196334"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee Yöntemi
Bu zincir tarafından çağrılan zinciri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChain`  
 dışı Çağrılan zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi. Bu zincir Şu anda yürütüliyorsa (yani, bu zincir, çağrılan bir zincirin dönmesi beklenmez) `ppChain` null olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu zincir, yürütmeyi devam etmeden önce çağrılan zincirin döndürülmesini bekler. Çağrılan zincir, çapraz iş parçacığı sıralanmış çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
