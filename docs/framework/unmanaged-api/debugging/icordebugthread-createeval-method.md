---
description: ': ICorDebugThread:: CreateEval yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a789840e099a14b584e5713bee12f5c4b0717fe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659393"
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
 dışı `ICorDebugEval` Bu iş parçacığının işlevlerini toplayan ve ortaya çıkaran nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Değerlendirme nesnesi, hesaplamayı yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir. Bu, değerlendirme tamamlanana kadar iş parçacığında gerçekleştirilmekte olan hesaplamayı keser.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
