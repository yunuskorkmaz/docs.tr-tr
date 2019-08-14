---
title: ICorProfilerInfo10 arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973752"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 arabirimi

İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[EnumerateObjectReferences yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır. |
|[Ifrozenobject yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler. |
|[GetLOHObjectSizeThreshold yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Yapılandırılan LOH eşiğinin değerini alır. |
|[RequestReJITWithInliners yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.  |
|[SuspendRuntime yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| GC yapmadan çalışma zamanını askıya alır. |
|[ResumeRuntime yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| GC yapmadan çalışma zamanını sürdürür. |

## <a name="requirements"></a>Gereksinimler  
**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Üst bilgi** CorProf. IDL, CorProf. h  
**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
