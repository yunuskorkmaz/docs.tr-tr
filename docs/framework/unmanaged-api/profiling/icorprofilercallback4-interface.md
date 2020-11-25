---
title: ICorProfilerCallback4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730298"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 Arabirimi

Ortak dil çalışma zamanının (CLR) bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReJITParameters Yöntemi](icorprofilercallback4-getrejitparameters-method.md)|Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.|  
|[MovedReferences2 Yöntemi](icorprofilercallback4-movedreferences2-method.md)|Sıkıştırma atık toplama işleminin sonucu olarak yığındaki nesnelerin yeni yerleşimini raporlar.|  
|[ReJITCompilationFinished Yöntemi](icorprofilercallback4-rejitcompilationfinished-method.md)|Profil oluşturucuyu, tam zamanında (JıT) derleyicisinin bir işlevin yeniden derlemesini tamamladığını bildirir.|  
|[ReJITCompilationStarted Yöntemi](icorprofilercallback4-rejitcompilationstarted-method.md)|Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.|  
|[ReJITError Yöntemi](icorprofilercallback4-rejiterror-method.md)|Yeniden derleme isteği işlenirken bir hatayla karşılaşıldı.|  
|[SurvivingReferences2 Yöntemi](icorprofilercallback4-survivingreferences2-method.md)|Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
