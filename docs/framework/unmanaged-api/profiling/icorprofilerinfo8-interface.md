---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo8 Interface'
title: ICorProfilerInfo8 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4538c9d314283c67ab0bfe6af3f3768062cffda4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646549"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 Arabirimi

Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[IsFunctionDynamic Metodu](icorprofilerinfo8-isfunctiondynamic-method.md)| Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.|
|[GetFunctionFromIP3 Metodu](icorprofilerinfo8-getfunctionfromip3-method.md)| Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler. Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir. |
|[GetDynamicFunctionInfo Metodu](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Dinamik yöntemler hakkında bilgi alır. |

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
