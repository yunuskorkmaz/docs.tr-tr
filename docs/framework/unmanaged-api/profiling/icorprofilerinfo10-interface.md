---
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863250"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 Arabirimi

İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](icorprofilerinfo9-interface.md) alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[EnumerateObjectReferences yöntemi](icorprofilerinfo10-enumerateobjectreferences-method.md)|Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır. |
|[Ifrozenobject yöntemi](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler. |
|[GetLOHObjectSizeThreshold yöntemi](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Yapılandırılan LOH eşiğinin değerini alır. |
|[RequestReJITWithInliners yöntemi](icorprofilerinfo10-requestrejitwithinliners-method.md)| İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.  |
|[SuspendRuntime yöntemi](icorprofilerinfo10-suspendruntime-method.md)| GC yapmadan çalışma zamanını askıya alır. |
|[ResumeRuntime yöntemi](icorprofilerinfo10-resumeruntime-method.md)| GC yapmadan çalışma zamanını sürdürür. |

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
