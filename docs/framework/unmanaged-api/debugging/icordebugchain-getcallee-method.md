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
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645306"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee Yöntemi
Bu zincir tarafından çağrıldı zinciri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
