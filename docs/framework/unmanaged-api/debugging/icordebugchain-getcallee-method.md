---
title: ICorDebugChain::GetCallee Metodu
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
ms.openlocfilehash: f050a3d9d37e43713c40896fb162bcf9932c6512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee Metodu
Bu zincir tarafından çağrıldı zinciri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppChain`  
 [out] Bir işaretçi adresine Icordebugchain nesnenin çağrılan zinciri temsil eder. (Diğer bir deyişle, bu zincirini geri dönmek çağrılan bir zincir için bekliyor değil ise) bu zincirini şu anda yürütülmekte, `ppChain` null olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu zincir çağrılan zinciri yürütme sürdürür önce dönmek bekler. Çağrılan zinciri, başka bir iş parçacığında iş parçacıkları arası sıralanmış çağrıları durumunda olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
