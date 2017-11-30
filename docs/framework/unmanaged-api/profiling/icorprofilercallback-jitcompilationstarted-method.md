---
title: "ICorProfilerCallback::JITCompilationStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12ae3e33d5553ed99a5a26b8fc872f0d07de81e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted Yöntemi
Profil Oluşturucu tam zamanında (JIT) derleyici bir işlev derlemek başlatıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Derleme başlatılıyor işlevi kimliği.  
  
 `fIsSafeToBlock`  
 [in] Profil Oluşturucu için engelleme olup olmadığını belirten bir değer çalışma zamanının işlemi etkiler. Değer `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir, aksi takdirde `false`.  
  
 Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarını eğme.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla Çifti almak mümkündür `JITCompilationStarted` ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) için her işlevi nedeniyle şekilde çalışma zamanı tanıtıcıları sınıf oluşturucuları çağırır. Örneğin, çalışma zamanı JIT derleme yöntemi A başlatır, ancak sınıf B sınıf oluşturucusu çalıştırılması gerekiyor. Bu nedenle, çalışma zamanı JIT derlerken Sınıf B oluşturucusu ve çalıştırır. Oluşturucusu çalışırken, yöntem yeniden JIT derlenmiş olması için bir neden olan bir yöntemine bir çağrı yapar. Bu senaryoda, A yönteminin ilk JIT derleme durdurulur. Ancak, her iki JIT derleme yöntemi A girişimleri JIT derleme olaylarla raporlanır. Profil Oluşturucu çağırarak yönteminin bir Microsoft Ara dili (MSIL) kodunu değiştirmek için edecekse [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi, bunu her ikisi için bunu gerekir `JITCompilationStarted` olayları, ancak aynı MSIL blok kullanabilir her ikisi için.  
  
 Profil oluşturucular JIT geri aramalar dizisini iki iş parçacığı aynı anda yapıyor geri aramalar olduğu durumlarda desteklemesi gerekir. Örneğin, iş parçacığı A çağırır `JITCompilationStarted`. Ancak, iş parçacığı A çağrıları önce `JITCompilationFinished`, iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) iş parçacığı A'ın işlevi Kimliğinden ile `JITCompilationStarted` geri çağırma. İşlev kimliği henüz geçerli olmamalıdır, görünebilir için yapılan bir çağrı `JITCompilationFinished` henüz Profil Oluşturucu tarafından almadı. Ancak, bunun gibi bir durumda, işlev kimliği geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Jıtcompilationfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
