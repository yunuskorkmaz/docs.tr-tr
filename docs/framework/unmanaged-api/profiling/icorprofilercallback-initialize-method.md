---
title: "ICorProfilerCallback::Initialize Yöntemi"
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
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a54ed382724b99fb4b2ae3a21d2d212379f55fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize Yöntemi
Yeni bir ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucu başlatmak üzere çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pICorProfilerInfoUnk`  
 [içinde](/cpp/atl/iunknown) profil oluşturucu için sorgu gerekir arabirimi bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirim işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `Initialize` Etkinleştirin (veya devre dışı bırak) değişmez geri aramalar yalnızca fırsatı çağrıdır. Bir geri çağırma tarafından etkinleştirildikten sonra `Initialize` çağrısı, bunu daha sonra kullanılarak devre dışı bırakılamaz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). COR_PRF_MONITOR_IMMUTABLE değeri [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırma gösterir hangi olayların değişmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Shutdown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
