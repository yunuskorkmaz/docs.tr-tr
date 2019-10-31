---
title: ICorDebugThread::GetID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: 48d2af96b50bf77347256b3d5860405e460a09d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133443"
---
# <a name="icordebugthreadgetid-method"></a>ICorDebugThread::GetID Yöntemi
Bu ICorDebugThread 'in etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwThreadId`  
 dışı İş parçacığının tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İşletim sistemi tanımlayıcısı bir işlemin yürütülmesi sırasında muhtemelen değişebilir ve iş parçacığının farklı bölümleri için farklı bir değer olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
