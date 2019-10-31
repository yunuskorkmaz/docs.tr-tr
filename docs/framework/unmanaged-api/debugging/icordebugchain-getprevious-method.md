---
title: ICorDebugChain::GetPrevious Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: c7598a9d93631ca93187886fd8929ba10726dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124731"
---
# <a name="icordebugchaingetprevious-method"></a>ICorDebugChain::GetPrevious Metodu
İş parçacığı için önceki çerçeve zincirini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChain`  
 dışı Bu iş parçacığı için önceki çerçeve zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi. Bu zincir ilk zincirdir `ppChain` null olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
