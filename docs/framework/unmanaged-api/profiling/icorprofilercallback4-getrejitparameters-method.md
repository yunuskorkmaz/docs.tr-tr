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
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865330"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters Yöntemi
Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan yöntemini içeren modül.  
  
 `methodId`  
 'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan metodun `MethodDef`.  
  
 `pFunctionControl`  
 'ndaki Profiler 'ın yeniden Derlenmekte olan yönteme yönelik JıT yeniden derleme bilgileri sağlamak için kullanabileceği [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, profil oluşturucunun belirli bir yöntemi yeniden derleme parametrelerini belirleyebilmesi için `GetReJITParameters` bir geri çağırma işlemini yayınlar. `GetReJITParameters` geri çağırması her işlev için yalnızca bir kez verilir; Profil Oluşturucu tarafından sağlanan parametreler, bu işlevin tüm örneklerine uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [JITCompilationStarted Yöntemi](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted Yöntemi](icorprofilercallback4-rejitcompilationstarted-method.md)
