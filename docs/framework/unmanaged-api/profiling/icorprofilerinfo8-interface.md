---
title: ICorProfilerInfo8 arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973695"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 arabirimi

Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[Ifunctiondynamic yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.|
|[GetFunctionFromIP3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler. Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir. |
|[Getdynamicfunctionınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Dinamik yöntemler hakkında bilgi alır. |

## <a name="requirements"></a>Gereksinimler  
**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi** CorProf. IDL, CorProf. h  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
