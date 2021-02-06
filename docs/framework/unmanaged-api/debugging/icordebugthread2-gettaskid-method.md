---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: getTaskId yöntemi'
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
ms.openlocfilehash: 5429daee9150d63834c747dd5ebb763dd6f0da6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658704"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID Yöntemi

Bu iş parçacığında çalışan görevin tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pTaskId`  
 dışı Bu ICorDebugThread2 nesnesi tarafından temsil edilen iş parçacığında çalışan görevin tanımlayıcısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir görev iş parçacığı üzerinde yalnızca iş parçacığı bağlantıyla ilişkilendirildiğinde çalıştırılabilir. `GetTaskID``pTaskId`iş parçacığı bir bağlantıyla ilişkilendirilmediği takdirde, içinde sıfır döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
