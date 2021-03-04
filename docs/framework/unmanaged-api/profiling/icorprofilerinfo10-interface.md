---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10 Interface'
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2fa0115f6894ac737696b63c1f0f00a0cb028ec
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106910"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 Arabirimi

İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](icorprofilerinfo9-interface.md) alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[EnumerateObjectReferences Metodu](icorprofilerinfo10-enumerateobjectreferences-method.md)|Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır. |
|[IsFrozenObject Metodu](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler. |
|[GetLOHObjectSizeThreshold Metodu](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Yapılandırılan LOH eşiğinin değerini alır. |
|[RequestReJITWithInliners Metodu](icorprofilerinfo10-requestrejitwithinliners-method.md)| İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.  |
|[SuspendRuntime Metodu](icorprofilerinfo10-suspendruntime-method.md)| GC yapmadan çalışma zamanını askıya alır. |
|[ResumeRuntime Metodu](icorprofilerinfo10-resumeruntime-method.md)| GC yapmadan çalışma zamanını sürdürür. |

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
