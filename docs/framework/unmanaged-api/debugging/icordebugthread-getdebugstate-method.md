---
title: ICorDebugThread::GetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: f054f8f2bd7c322e722a1e17290ba6fbad9e37b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133516"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState Yöntemi
Bu ICorDebugThread nesnesinin geçerli hata ayıklama durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pState`  
 dışı Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem şu anda durdurulmuşsa, bu iş parçacığının gerçek geçerli durumu değil, işlem devam etseydi, bu iş parçacığı için mevcut olacak hata ayıklama durumunu temsil `pState`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
