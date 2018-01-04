---
title: "ICorDebugThread2::InterceptCurrentException Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.InterceptCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aaf02ed27ba87f39e5168854254191388d17019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException Yöntemi
Bir hata ayıklayıcısı geçerli özel durumun bu iş parçacığında izlemesine izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFrame`  
 [in] Etkin yığın çerçevesi temsil eden bir Icordebugframe gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `InterceptCurrentException` Yöntemi bir özel durum geri çağırma arasında çağrılabilir ([Icordebugmanagedcallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) veya [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) ve ilişkili çağrısı [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
