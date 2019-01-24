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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65c18f534771407b2dcf4710e2604e0b30cbdcdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611052"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil oluşturucu içinde ekleyeceğiniz derleme başvuruları, ortak dil çalışma zamanı (CLR) bildirmek profil oluşturucu sağlar [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddAssemblyReference Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|CLR Profil Oluşturucu ekleme planları bir bütünleştirilmiş kod başvurusu bildirir [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR Profil Oluşturucu geçirmeden bir `ICorProfilerAssemblyReferenceProvider` arabirimi nesnesinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma. CLR Profil Oluşturucu, daha sonra eklenecek planları derleme başvuruları bildirmek profil oluşturucu böylece [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md). geri çağırma. Bu, CLR'nin bütünleştirilmiş kod başvurusu kapanış walker ve derlemeleri paylaşılabilir olup olmadığını belirlemek için kendi algoritmaları doğruluğu artırır.  
  
 Bu arabirim yalnızca kullanılabilir [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma profil oluşturucu için bu arabirimi nesnesini geçirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
