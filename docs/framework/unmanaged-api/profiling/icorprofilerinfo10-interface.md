---
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175076"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 Arabirimi

[ICorProfilerInfo9'un](icorprofilerinfo9-interface.md) işlev IL'sini değiştirme, çalışma zamanındaki sorgu bilgilerini ve çalışma süresini askıya alma ve devam ettirme yöntemleri sağlayan bir alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[EnumerateObjectReferences Metodu](icorprofilerinfo10-enumerateobjectreferences-method.md)|ObjectID, geri arama ve istemciData göz önüne alındığında, her nesne başvuru (varsa) numarasılandırır. |
|[IsFrozenObject Metodu](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID verildiğinde, nesnenin salt okunur segmentte olup olmadığını belirler. |
|[GetLOHObjectSizeThreshold Metodu](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Yapılandırılan LOH eşiğinin değerini alır. |
|[RequestReJITWithInliners Metodu](icorprofilerinfo10-requestrejitwithinliners-method.md)| İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir inliners rejits.  |
|[SuspendRuntime Metodu](icorprofilerinfo10-suspendruntime-method.md)| GC gerçekleştirmeden çalışma süresini askıya aldı. |
|[ResumeRuntime Metodu](icorprofilerinfo10-resumeruntime-method.md)| GC gerçekleştirmeden çalışma süresini devam ettirer. |

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri.](../../../core/install/dependencies.md?pivots=os-windows)  
**Üstbilgi:** CorProf.idl, CorProf.h  
**.NET Sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
