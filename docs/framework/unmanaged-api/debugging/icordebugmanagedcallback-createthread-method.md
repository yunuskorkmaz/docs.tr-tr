---
title: "ICorDebugManagedCallback::CreateThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8acb12d216949fc4e0636b5a2c28657ef5c79bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a>ICorDebugManagedCallback::CreateThread Yöntemi
Hata ayıklayıcı bir iş parçacığı yönetilen kod yürütmeyi başlattı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] İş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesnesi için bir işaretçi.  
  
 `thread`  
 [in] Bir işaretçi Icordebugthread nesneye iş parçacığını temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacığı yürütülecek ilk yönetilen kod yönerge yerleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
