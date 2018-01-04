---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi
Hata ayıklayıcı kod yürütmeyi bir dizi noktası düzenlenen işlevi daha eski bir sürümünde ulaştı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye düzenlenen işlevi içeren uygulama etki alanını temsil eder.  
  
 `pThread`  
 [in] Bir işaretçi Icordebugthread nesneye eşleme kesme noktası karşılaşıldı iş parçacığı temsil eder.  
  
 `pOldFunction`  
 [in] Bir işaretçi ICorDebugFunction nesneye iş parçacığı üzerinde çalışmakta olan işlevi sürümünü temsil eder.  
  
 `pNewFunction`  
 [in] Bir işaretçi ICorDebugFunction nesneye işlevi, en son sürümünü temsil eder.  
  
 `oldILOffset`  
 [in] Yönerge işaretçisi işlevi eski bir sürümünde Microsoft Ara dili (MSIL) uzaklığı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma hata ayıklayıcı çağırarak uygun yeni sürümü belirtilen işlev, yerinde yönerge işaretçisine yeniden eşlemek için bir fırsat sunar [Icordebugılframe2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) yöntemi. Hata ayıklayıcı değil çağırırsanız `RemapFunction` çağırmadan önce [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi, çalışma zamanı eski kod yürütülmeye devam eder ve başka ateşlenir `FunctionRemapOpportunity` sonraki dizisi noktasına geri çağırma.  
  
 Bu geri çağırma hata ayıklayıcı S_OK dönene kadar verilen işlev daha eski bir sürümü yürütülen her çerçevesi için çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
