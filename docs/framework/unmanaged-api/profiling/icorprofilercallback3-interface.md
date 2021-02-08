---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback3 Interface'
title: ICorProfilerCallback3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 70fba8768fef5da411b566d918308989a3f6e863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788806"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3 Arabirimi

Ortak dil çalışma zamanının (CLR) profil oluşturucuya iliştirme ve ayır durum bilgilerini iletişim kurmak için kullandığı geri çağırma yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[InitializeForAttach Yöntemi](icorprofilercallback3-initializeforattach-method.md)|Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için CLR tarafından çağırılır.|  
|[ProfilerAttachComplete Yöntemi](icorprofilercallback3-profilerattachcomplete-method.md)|Profiler tarafından, profil oluşturucunun artık yakalama yöntemlerini çağırabelirteolabileceğini göstermek için çağırılır.|  
|[ProfilerDetachSucceeded Yöntemi](icorprofilercallback3-profilerdetachsucceeded-method.md)|Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
