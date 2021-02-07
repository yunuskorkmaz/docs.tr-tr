---
description: ': ICorProfilerFunctionControl arabirimi hakkında daha fazla bilgi edinin'
title: ICorProfilerFunctionControl Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 7b4ac58d2b8754108b4e10493596776987a93a49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753321"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl Arabirimi

Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretmelidir denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmasına imkan tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetCodegenFlags Yöntemi](icorprofilerfunctioncontrol-setcodegenflags-method.md)|Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.|  
|[SetILFunctionBody Yöntemi](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.|  
|[SetILInstrumentedCodeMap Yöntemi](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Belirtilen ortak ara dil (CıL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorProfilerFunctionControl`Arabirimi, tek bir yeniden derlenmiş işlev için kod oluşturmayı denetlemek için yöntemler sağlar. Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır. Her bir örneği `ICorProfilerFunctionControl` bir işlevin tüm örneklerini denetler.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumJITedFunctions2 Yöntemi](icorprofilerinfo4-enumjitedfunctions2-method.md)
