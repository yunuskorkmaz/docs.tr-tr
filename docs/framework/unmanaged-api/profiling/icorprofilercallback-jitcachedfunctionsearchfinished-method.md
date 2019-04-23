---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122947"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
Profil Oluşturucu, arama Native Image Generator (NGen.exe) kullanarak önceden derlenen bir işlev için tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Aramanın gerçekleştirildiği işlevi kimliği.  
  
 `result`  
 [in] Değerini [cor_prf_jıt_cache](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) arama sonucunu gösteren sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0 [Icorprofilercallback::jıtcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri çağırmaları değil oluşturulacak normal NGen görüntülerinin tüm işlevler için. Yalnızca bir profil oluşturucu için en iyi duruma getirilmiş NGen görüntülerinin geri çağırmaları tüm işlevler görüntüde oluşturur. Ancak, yalnızca derlenmiş just-in-time (JIT) gereken işlevi zorlamak için bu geri aramalarda kullanmaya çalışırsa, ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu için iyileştirilmiş NGen görüntülerinin istemelidir. Aksi takdirde, profil oluşturucu işlevi bilgileri toplamak için yavaş bir strateji kullanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
