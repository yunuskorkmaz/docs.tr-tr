---
title: ICorProfilerCallback4::GetReJITParameters Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f628bd1270b529264c14236ca7cdc03bf7afd9d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454212"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters Metodu
Yeni bir derlenmiş yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamak Kod Oluşturucu sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] JIT derleme parametreleri için CLR gerekiyor yöntemi içeren modülü.  
  
 `methodId`  
 [in] `MethodDef` CLR gereken JIT derleme parametreleri yöntemi.  
  
 `pFunctionControl`  
 [in] Bir işaretçi bir [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) profil oluşturucu yeniden derlenmesi yöntemi JIT derleme bilgilerini sağlamak için kullanabileceğiniz arabirimi.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR sorunları bir `GetReJITParameters` geri çağırma böylece profil oluşturucu belirli bir yöntemin yeniden derlenmesi için parametreleri belirtebilirsiniz. `GetReJITParameters` Geri çağırma işlevi yalnızca bir kez verildiği; bu işlev tüm örneklerini Profil Oluşturucu tarafından sağlanan parametreleri uygulayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [ReJITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
