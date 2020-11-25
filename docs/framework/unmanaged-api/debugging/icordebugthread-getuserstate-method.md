---
title: ICorDebugThread::GetUserState Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: dd3936656ce1c9482b7f07a5780fcf651356b4be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727971"
---
# <a name="icordebugthreadgetuserstate-method"></a>ICorDebugThread::GetUserState Metodu

Bu ICorDebugThread 'in geçerli kullanıcı durumunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pState`  
 dışı Bu iş parçacığının geçerli kullanıcı durumunu tanımlayan, CorDebugUserState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 İş parçacığının kullanıcı durumu, hata ayıklamakta olan program tarafından incelenmekte olan iş parçacığının durumudur. Bir iş parçacığında birden fazla durum bitleri ayarlanmış olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
