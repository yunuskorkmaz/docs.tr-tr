---
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
ms.openlocfilehash: 1286ce953c96eb3e3164ba5b209031dd1ec5c453
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864706"
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
 `ICorProfilerFunctionControl` arabirimi, tek bir yeniden derlenmiş işlev için kod oluşturmayı denetlemek için yöntemler sağlar. Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır. Her bir `ICorProfilerFunctionControl` örneği, bir işlevin tüm örneklerini denetler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumJITedFunctions2 Yöntemi](icorprofilerinfo4-enumjitedfunctions2-method.md)
