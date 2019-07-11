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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79743b78ea3d19bab4756b580d2feddd07e0a23b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745015"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee Yöntemi
Bu zincir tarafından çağrıldı zinciri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChain`  
 [out] Çağrılan zincirini temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi. Bu zincir (diğer bir deyişle, bu zincir döndürmek çağrılan bir zincirinde beklemiyorsa) şu anda yürütülüyorsa `ppChain` null olacaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu zincir yürütmeyi devam ettirir önce döndürmek çağrılan zinciri için bekler. Çağrılan zinciri sıralanmış iş parçacıkları arası çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
