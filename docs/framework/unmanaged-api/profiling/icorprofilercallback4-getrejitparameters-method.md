---
title: ICorProfilerCallback4::GetReJITParameters Yöntemi
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
ms.openlocfilehash: 7aae292daefe9333585a50d1d8c9ce49b1008cd9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470789"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters Yöntemi
Kod profil oluşturucu, yeni bir znovu yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamanızı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] Kendisi için CLR JIT yeniden derleme parametreleri gereken yöntemini içeren modül.  
  
 `methodId`  
 [in] `MethodDef` Yönteminin CLR JIT yeniden derleme parametreleri gerekir.  
  
 `pFunctionControl`  
 [in] Bir işaretçi bir [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) profil oluşturucuyu yeniden derlenen yöntem JIT yeniden derleme bilgilerini sağlamak için kullanabileceğiniz arabirimi.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR sorunları bir `GetReJITParameters` geri çağırma profil oluşturucu, belirli bir yöntemin yeniden derlemeden parametrelerini belirtebilirsiniz. `GetReJITParameters` Geri çağırma işlevi yalnızca bir kez verildiği; Profil Oluşturucu tarafından sağlanan parametreleri, bu işlevin tüm örneklerine uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
