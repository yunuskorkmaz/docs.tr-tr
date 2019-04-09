---
title: ICorProfilerFunctionControl::SetCodegenFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104448"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags Yöntemi
Bir veya daha fazla bayraklarını ayarlar [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırması için bir tam zamanında (JIT) denetimi kod oluşturma için yeniden derlenen işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir veya daha fazla bayrakları [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu bu arabirimi üzerinden bir örneğini alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma. `SetCodegenFlags` kod oluşturma için znovu işlevi denetlemek profil oluşturucu sağlar. Tüm diğer JIT yeniden derleme parametreleri gibi kod oluşturma bayrakları işlevin tüm örneklerine uygulanır.  
  
 JIT Derleyici bir işlevi derlenirken başka bir kaynak tarafından belirtilen diğer bayraklar yanı sıra bu derleme bayraklar göz önünde bulundurur.  Hata ayıklayıcı diğer kaynaklar dahil, Profil Oluşturucu tarafından başlangıçta tarafından ayarlanmış kullanarak genel bayraklar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi (değerlerle `COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS`) ve profil oluşturucunun [ Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırma.  JIT derleyicisi istekleri en iyi duruma getirme, en az bir kaynak için öncelik verir.  Örneğin, profil oluşturucu belirtiyorsa `COR_PRF_DISABLE_INLINING` başlangıçta belirttiğinde ancak `COR_PRF_CODEGEN_DISABLE_INLINING` içinde [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) geri çağırma, satır içi kullanım yine de devre dışı.  Benzer şekilde, profil oluşturucu belirttiğini `COR_PRF_CODEGEN_DISABLE_INLINING` içinde `SetCodegenFlags`, ancak sonra devre dışı bırakır kullanarak satır içi [Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırma, satır içi kullanım dışıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
