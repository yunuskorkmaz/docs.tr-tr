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
ms.openlocfilehash: 2cee012be2665f5a7212600ec11e401b18160d8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691402"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider Arabirimi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profiler 'ın, profil oluşturucunun [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularının ortak dil çalışma ZAMANıNı (CLR) bilgilendirmesini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddAssemblyReference Yöntemi](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|Profiler planlarına eklenen ve [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırmasına Eklenecek derleme başvurusunun clr 'sini bilgilendirir.|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR, `ICorProfilerAssemblyReferenceProvider` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında profil oluşturucu bir arabirim nesnesine geçirir. Bu, profil oluşturucunun Profiler planının CLR 'yi [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)içinde eklemesi için derleme başvurularını bilgilendirmesini sağlar. callback. Bu, CLR 'nin derleme başvurusu kapatma denetçisi ve derlemelerin paylaşılıp paylaşılamayacağını belirlemek için algoritmalarının doğruluğunu geliştirir.  
  
 Bu arabirim yalnızca bu arabirim nesnesini Profiler 'a geçiren [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
