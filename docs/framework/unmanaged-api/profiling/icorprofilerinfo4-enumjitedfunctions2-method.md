---
title: "ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9b9c8739a8ab47b4e24dba1b15c228d2800290d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi
JIT derlenmiş ve JIT yeniden derlenmesi daha önce tüm işlevleri için bir numaralandırıcı döndürür. Bu yöntem değiştirir [Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) JIT yeniden derlenmesi kimlikleri listeleme değil yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi. Döndürülen numaralandırma değerlerini içeren `COR_PRF_FUNCTION::reJitId` alan. [Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) bu yöntemi değiştirir, yöntem değil listeleme JIT yeniden derlenmesi kimlikleri, çünkü `COR_PRF_FUNCTION::reJitId` alanı her zaman 0 olarak ayarlayın. `ICorProfilerInfo4::EnumJITedFunctions` Yöntemi nedeniyle JIT yeniden derlenmesi kimlikleri, listeleme `COR_PRF_FUNCTION::reJitId` alanını düzgün şekilde ayarlayın. Unutmayın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi, bir atık toplama tetikleyebilir, ancak [Icorprofilerınfo3::enumjıtedfunctions yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) almayacak.  Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Enumjıtedfunctions yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [Icorprofilerınfo4 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
