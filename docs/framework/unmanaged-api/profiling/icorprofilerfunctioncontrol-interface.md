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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211445"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl Arabirimi
Bir kod profil oluşturucu nasıl JIT Derleyici kodu belirli bir yöntem yeniden derlemeden oluşturmasını denetlemek için (CLR) ortak dil çalışma zamanıyla iletişim kurmasına izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetCodegenFlags Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Bir veya daha fazla bayraklarını ayarlar [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırması için bir tam zamanında (JIT) denetimi kod oluşturma için yeniden derlenen işlevi.|  
|[SetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.|  
|[SetILInstrumentedCodeMap Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Belirtilen işlev için kod haritası, belirtilen ortak Ara dil (CIL) map girişlerini kullanarak ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerFunctionControl` Arabirimi kod oluşturma için tek bir znovu işlevi denetlemek için yöntemler sağlar. Profil Oluşturucu bu arabirimi üzerinden bir örneğini alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma. Her bir örneği `ICorProfilerFunctionControl` bir işlevin tüm örneklerini denetler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
