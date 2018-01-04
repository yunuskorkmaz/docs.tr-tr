---
title: "ICorDebugThread::CreateEval Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval Yöntemi
Toplar ve bu Icordebugthread işlevselliği kullanıma sunan bir Icordebugeval nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEval`  
 [out] Adresine bir işaretçi bir `ICorDebugEval` toplar ve bu iş parçacığı işlevselliği kullanıma sunan bir nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerlendirme nesne kendi hesaplama yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir. Bu değerlendirme tamamlanana kadar iş parçacığı üzerinde şu anda gerçekleştirilen hesaplama kesintiye uğratır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
