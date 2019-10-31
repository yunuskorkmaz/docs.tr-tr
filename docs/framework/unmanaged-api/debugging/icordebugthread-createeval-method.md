---
title: ICorDebugThread::CreateEval Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133611"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval Yöntemi
Bu ICorDebugThread 'in işlevlerini toplayan ve sunan bir ıcordebugger Geval nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEval`  
 dışı Bu iş parçacığının işlevlerini toplayan ve ortaya çıkaran `ICorDebugEval` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerlendirme nesnesi, hesaplamayı yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir. Bu, değerlendirme tamamlanana kadar iş parçacığında gerçekleştirilmekte olan hesaplamayı keser.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
