---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174310"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
Profil Oluşturucu, arama Native Image Generator (NGen.exe) kullanarak önceden derlenen bir işlev için başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Aramanın gerçekleştirildiği işlevi kimliği.  
  
 `pbUseCachedFunction`  
 [out] `true` yürütme altyapısı, (varsa) bir işlev önbelleğe alınmış sürümünü kullanmanız gerekir, aksi takdirde `false`. Değer ise `false`, JIT olarak derlenmiş değil bir sürümünü kullanmak yerine, işlevi yürütme altyapısı JIT derlenir.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0 `JITCachedFunctionSearchStarted` ve [Icorprofilercallback::jıtcachedfunctionsearchfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları değil oluşturulacak normal NGen görüntülerinin tüm işlevler için. Bir profil için en iyi duruma getirilmiş NGen görüntülerinin geri çağırmaları tüm işlevler görüntüde oluşturur. Ancak, yalnızca derlenmiş just-in-time (JIT) gereken işlevi zorlamak için bu geri aramalarda kullanmaya çalışırsa, ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu için iyileştirilmiş NGen görüntülerinin istemelidir. Aksi takdirde, profil oluşturucu işlevi bilgileri toplamak için yavaş bir strateji kullanmalıdır.  
  
 Profil Oluşturucular, burada, profili oluşturulmuş bir uygulama birden çok iş parçacığı aynı yöntemi aynı anda aradığınız çalışmaları desteklemesi gerekir. Örneğin, bir iş parçacığı çağrı `JITCachedFunctionSearchStarted` ve profil oluşturucu ayarlayarak yanıt *pbUseCachedFunction*JIT derlemesi zorlamak için false. Bir daha sonra çağıran iş parçacığı [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Artık B çağrılar iş parçacığı `JITCachedFunctionSearchStarted` aynı işlevi. Profil Oluşturucu Niyet JIT derleme işlevi için belirtilen olsa da, profil oluşturucu için iş parçacığı A çağrısına yanıtladı önce geri çağırma iş parçacığı B gönderdiği için profil oluşturucu ikinci geri çağırma alır `JITCachedFunctionSearchStarted`. İş parçacıklarını nasıl zamanlanmış iş parçacıklarını çağrı nasıl siparişe bağlıdır.  
  
 Profil oluşturucuyu yinelenen geri çağırmaları aldığında tarafından başvurulan değer ayarlamalısınız `pbUseCachedFunction` için yinelenen tüm geri çağırmalar için aynı değeri. Diğer bir deyişle, `JITCachedFunctionSearchStarted` birden çok kez aynı adlı `functionId` değeri, profil oluşturucu her zaman aynı yanıt vermelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
