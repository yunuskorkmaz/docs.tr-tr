---
title: ICorProfilerCallback::JITCompilationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530764"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished Yöntemi
Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi derleme işleminin tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Derlenen işlevi kimliği.  
  
 `hrStatus`  
 [in] Derleme başarılı olup olmadığını belirten bir değer.  
  
 `fIsSafeToBlock`  
 [in] Profil oluşturucuya engelleme olup olmadığını belirten bir değer çalışma zamanı işleyişini etkiler. Değer `true` engelleme, bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabilir, aksi takdirde, `false`.  
  
 Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarından eğriltilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
