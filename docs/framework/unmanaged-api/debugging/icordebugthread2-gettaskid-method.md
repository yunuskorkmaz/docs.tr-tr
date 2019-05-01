---
title: ICorDebugThread2::GetTaskID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417f99c2b9fa7e77f8696c27cb3929c92956c08c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946358"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID Yöntemi
Bu iş parçacığı üzerinde çalışan görev tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pTaskId`  
 [out] Bu Icordebugthread2 nesnesiyle temsil edilen iş parçacığı üzerinde çalışan görev tanımlayıcısı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir görev, yalnızca iş parçacığı bir bağlantı ile ilişkili ise iş parçacığı üzerinde çalışabilir. `GetTaskID` sıfır döndürür `pTaskId` iş parçacığı bir bağlantıyla ilişkili değilse.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
