---
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
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865577"
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
