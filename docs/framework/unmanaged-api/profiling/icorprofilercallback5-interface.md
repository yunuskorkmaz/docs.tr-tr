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
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499213"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 Arabirimi
Bir profil oluşturucunun, ICorProfilerCallback:: [ObjectReferences](icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleriyle birlikte [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) veya [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi ile birlikte kullanıldığında, canlı nesnelerin tam kapatılmasını belirlemesine yardımcı olmak için bilgileri tamamlar.  
  
 `ICorProfilerCallback5`bağımlı tanıtıcılarla ilgili bildirimlere abone olmak için yönetilen bir bellek Oluşturucu tarafından uygulanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences Yöntemi](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Doğrudan üye alan başvuruları ve bağımlılıklar aracılığıyla bu köklerin başvurduğu nesnelerin geçişli kapanışını tanımlar `ConditionalWeakTable` .|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
