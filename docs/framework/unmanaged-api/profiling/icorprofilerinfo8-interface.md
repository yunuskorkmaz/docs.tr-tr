---
title: ICorProfilerInfo8 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868323"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 Arabirimi

Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[Ifunctiondynamic yöntemi](icorprofilerinfo8-isfunctiondynamic-method.md)| Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.|
|[GetFunctionFromIP3 yöntemi](icorprofilerinfo8-getfunctionfromip3-method.md)| Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler. Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir. |
|[Getdynamicfunctionınfo yöntemi](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Dinamik yöntemler hakkında bilgi alır. |

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
