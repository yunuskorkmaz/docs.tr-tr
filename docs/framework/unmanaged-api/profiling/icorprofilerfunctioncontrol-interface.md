---
title: ICorProfilerFunctionControl Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 043e97595ba29d0fb5320b8f1bdc4aad4f755067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl Arabirimi
Ortak dil çalışma zamanı ile nasıl JIT Derleyici kodu belirli bir yöntemi yeniden derlenmesi sırasında oluşturulmasına denetlemek için (CLR) iletişim kurmak bir kod profil oluşturucu izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetCodegenFlags Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Bir veya daha fazla bayraklarını ayarlar [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) denetim kod oluşturma için bir tam zamanında (JIT) numaralandırma işlevi yeniden derlenebileceğini gösterir.|  
|[SetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.|  
|[SetILInstrumentedCodeMap Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Kod Haritası belirtilen işlev için belirtilen ortak Ara dili (CIL) eşleme girdilerini kullanarak ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerFunctionControl` Arabirimi kod oluşturma için tek bir derlenmiş işlevi denetlemek için yöntemler sağlar. Profil Oluşturucu bu arabirimi aracılığıyla örneği alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma. Her örneği `ICorProfilerFunctionControl` bir işlev tüm örneklerini denetler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumJITedFunctions2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
