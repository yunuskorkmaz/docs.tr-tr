---
title: "ICorDebugThread::CreateStepper Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 869b1862e479c42c1ea43c90a276e95adcd5c321
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper Yöntemi
Bu Icordebugthread etkin çerçevesi atlama izin veren bir ICorDebugStepper nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppStepper`  
 [out] Adresine bir işaretçi bir `ICorDebugStepper` bu iş parçacığının etkin çerçevesi atlama izin veren nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen kod etkin çerçeveyi olabilir.  
  
 `ICorDebugStepper` Arabirimi, gerçek atlama gerçekleştirmek için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
