---
title: ICorProfilerCallback::JITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5eb881c8f024373fbff1dad17cd883ab6cafa2a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466642"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted Yöntemi
Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi derlemeye ne başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kendisi için derleme başlatılıyor işlevi kimliği.  
  
 `fIsSafeToBlock`  
 [in] Profil oluşturucuya engelleme olup olmadığını belirten bir değer çalışma zamanı işleyişini etkiler. Değer `true` engelleme, bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabilir, aksi takdirde, `false`.  
  
 Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarından eğriltilebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla çiftinin almak mümkündür `JITCompilationStarted` ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) her işlev için şekli nedeniyle çalışma zamanı işleyen sınıf oluşturucuları çağırır. Örneğin, çalışma zamanı JIT derleme yöntemine bir başlatmaz, bunun Sınıf B sınıf oluşturucusu çalıştırılması gerekiyor. Bu nedenle, çalışma zamanı JIT derlenir B sınıfı için oluşturucu ve çalıştırır. Oluşturucu çalışırken yöntemi yeniden JIT olarak derlenmiş olması için bir neden olan bir yönteme bir çağrı yapar. Bu senaryoda, bir yöntemin ilk JIT derlemesi durdurulur. Ancak, her iki JIT derleme yöntemi bir girişimi JIT derlemesi olaylarla raporlanır. Profil Oluşturucu çağırarak yöntemi bir Microsoft Ara dili (MSIL) kodu yerine yayınlanıyorsa [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi, her ikisi için bunu gerekir `JITCompilationStarted` olaylar, ancak aynı MSIL bloğundan kullanabilir her ikisi için.  
  
 Profil oluşturucular JIT geri çağırmalar dizisi, burada iki iş parçacığı geri çağırmaları aynı anda çağırıyorsanız durumlarda desteklemesi gerekir. Örneğin, bir iş parçacığı çağrı `JITCompilationStarted`. Ancak, bir dizi çağrıları önce `JITCompilationFinished`, iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) A'ın iş parçacığından işlevi kimlikli `JITCompilationStarted` geri çağırma. İşlev kimliği henüz geçerli gerektiğini görünebilir çünkü bir çağrı `JITCompilationFinished` henüz Profil Oluşturucu tarafından almadı. Ancak, bunun gibi bir durumda, işlev kimliği geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
