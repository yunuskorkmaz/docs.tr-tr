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
ms.openlocfilehash: 88c9f552b73af69ea4e1f64b75ed74ea762dcdfb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429932"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags Yöntemi
Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 'ndaki [Cor_prf_codegen_flags](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak.  
  
## <a name="remarks"></a>Açıklamalar  
 Profiler, [ICorProfilerCallback4:: GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır. `SetCodegenFlags`, profil oluşturucunun yeniden derlenmiş işlev için kod oluşturmayı denetlemesine izin verir. Diğer tüm JıT yeniden derleme parametrelerinde olduğu gibi, kod oluşturma bayrakları işlevin tüm örneklerine uygulanır.  
  
 JıT derleyicisi, bir işlev derlenirken diğer kaynaklar tarafından belirtilen diğer bayraklarla birlikte bu derleme bayraklarını dikkate alır.  Diğer kaynaklar, [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi (`COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS`) ve profil oluşturucunun [ICorProfilerCallback:: jıntıl](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırması kullanılarak başlangıçta profil oluşturucu tarafından ayarlanan hata ayıklayıcıyı, genel bayrakları içerir.  JıT derleyicisi en az en iyileştirme miktarını isteyen bir kaynağa öncelik verir.  Örneğin, profil oluşturucu başlangıçta `COR_PRF_DISABLE_INLINING` belirtirse, ancak [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) geri aramasında `COR_PRF_CODEGEN_DISABLE_INLINING` belirtmezse, satır içi hala devre dışı bırakılmıştır.  Benzer şekilde, profil oluşturucu `SetCodegenFlags``COR_PRF_CODEGEN_DISABLE_INLINING` belirtmezse, ancak [ICorProfilerCallback:: jınkıx](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırma özelliğini kullanarak geçersiz kılma işlemini devre dışı bırakır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
