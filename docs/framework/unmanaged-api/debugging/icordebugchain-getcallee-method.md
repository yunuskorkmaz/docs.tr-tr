---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugzincirine:: Getçağrılan yöntemi'
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
ms.openlocfilehash: 4787893c86804c648dae14bf2e6f7425808104b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661434"
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
 dışı Çağrılan zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi. Bu zincir Şu anda yürütüliyorsa (yani, bu zincir, çağrılan bir zincirin dönmesi beklenmez), `ppChain` null olur.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu zincir, yürütmeyi devam etmeden önce çağrılan zincirin döndürülmesini bekler. Çağrılan zincir, çapraz iş parçacığı sıralanmış çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
