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
ms.openlocfilehash: 527e48d02d5267d6ae41214686c2e8c997d85dca
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499551"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters Yöntemi
Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan yöntemini içeren modül.  
  
 `methodId`  
 'ndaki `MethodDef`Clr 'nın JIT yeniden derleme parametrelerine ihtiyacı olan yöntemi.  
  
 `pFunctionControl`  
 'ndaki Profiler 'ın yeniden Derlenmekte olan yönteme yönelik JıT yeniden derleme bilgileri sağlamak için kullanabileceği [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `GetReJITParameters` profil oluşturucunun belirli bir yöntemi yeniden derleme parametrelerini belirleyebilmesi için bir geri çağırma işlemini yayınlar. `GetReJITParameters`Geri çağırma, işlev başına yalnızca bir kez verilir; profil oluşturucu tarafından sağlanan parametreler, bu işlevin tüm örneklerine uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [JITCompilationStarted Yöntemi](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted Yöntemi](icorprofilercallback4-rejitcompilationstarted-method.md)
