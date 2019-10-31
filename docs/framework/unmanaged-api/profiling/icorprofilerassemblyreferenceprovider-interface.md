---
title: ICorProfilerAssemblyReferenceProvider Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: f5ba72dca25889fb57c0ae1bb2429e54a8cf2228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128711"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profiler 'ın, profil oluşturucunun [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularının ortak dil çalışma ZAMANıNı (CLR) bilgilendirmesini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddAssemblyReference Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|Profiler planlarına eklenen ve [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırmasına Eklenecek derleme başvurusunun clr 'sini bilgilendirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, profil oluşturucuyu [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasında bir `ICorProfilerAssemblyReferenceProvider` Interface nesnesine geçirir. Bu, profil oluşturucunun Profiler planının CLR 'yi [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)içinde eklemesi için derleme başvurularını bilgilendirmesini sağlar. callback. Bu, CLR 'nin derleme başvurusu kapatma denetçisi ve derlemelerin paylaşılıp paylaşılamayacağını belirlemek için algoritmalarının doğruluğunu geliştirir.  
  
 Bu arabirim yalnızca bu arabirim nesnesini Profiler 'a geçiren [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasında kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
