---
title: "ICorProfilerFunctionControl::SetCodegenFlags Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetCodegenFlags
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9264e717da62c88b6f2f6eca262b5635fc928741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags Yöntemi
Bir veya daha fazla bayraklarını ayarlar [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) denetim kod oluşturma için bir tam zamanında (JIT) numaralandırma işlevi yeniden derlenebileceğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir veya daha fazla bayraklarını [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu bu arabirimi aracılığıyla örneği alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma. `SetCodegenFlags`derlenmiş işlevi için kod oluşturmanın denetlemek profil oluşturucu sağlar. Tüm diğer JIT derleme parametrelerle birlikte gibi kod oluşturma bayrakları işlevi tüm örneklerine uygulanır.  
  
 JIT Derleyici bir işlev derlenirken başka bir kaynak tarafından belirtilen diğer bayraklar yanı sıra bu Derleme bayrakları göz önünde bulundurur.  Hata ayıklayıcı diğer kaynaklar dahil, Profil Oluşturucu tarafından başlangıçta tarafından belirlenen kullanarak genel bayraklar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi (değerlerle `COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS`) ve profil oluşturucu 's [ Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırma.  JIT Derleyici istekleri en iyi duruma getirme, en az bir kaynak için öncelik verir.  Örneğin, profil oluşturucu belirtiyorsa `COR_PRF_DISABLE_INLINING` başlangıçta, belirtmediği ancak `COR_PRF_CODEGEN_DISABLE_INLINING` içinde [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) geri arama, satır içi kullanım hala devre dışı.  Benzer şekilde, profil oluşturucu belirttiğini `COR_PRF_CODEGEN_DISABLE_INLINING` içinde `SetCodegenFlags`, ancak sonra devre dışı bırakır kullanarak satır içi kullanım [Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri arama, satır içi kullanım dışıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
