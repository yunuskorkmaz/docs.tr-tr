---
title: ICorProfilerCallback5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865031"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 Arabirimi
Bir profil oluşturucunun, ICorProfilerCallback:: [ObjectReferences](icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleriyle birlikte [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) veya [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi ile birlikte kullanıldığında, canlı nesnelerin tam kapatılmasını belirlemesine yardımcı olmak için bilgileri tamamlar.  
  
 bağımlı tanıtıcılarla ilgili bildirimlere abone olmak için `ICorProfilerCallback5` yönetilen bir bellek Oluşturucu tarafından uygulanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences Yöntemi](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Doğrudan üye alan başvuruları ve `ConditionalWeakTable` bağımlılıklarıyla, bu köklerin başvurduğu nesnelerin geçişli kapatılmasını belirler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
