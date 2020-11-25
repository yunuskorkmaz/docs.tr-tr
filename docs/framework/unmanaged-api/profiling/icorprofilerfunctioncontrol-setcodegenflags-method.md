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
ms.openlocfilehash: 3593b07759b4d6feee239042e5aabaf0876fdd1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716310"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags Yöntemi

Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flags`  
 'ndaki [Cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak.  
  
## <a name="remarks"></a>Açıklamalar  

 Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır. `SetCodegenFlags` profil oluşturucunun, yeniden derlenmiş işlev için kod oluşturmayı denetlemesine izin verir. Diğer tüm JıT yeniden derleme parametrelerinde olduğu gibi, kod oluşturma bayrakları işlevin tüm örneklerine uygulanır.  
  
 JıT derleyicisi, bir işlev derlenirken diğer kaynaklar tarafından belirtilen diğer bayraklarla birlikte bu derleme bayraklarını dikkate alır.  Diğer kaynaklar, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini (değerleri `COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS` ) ve profil oluşturucunun [ICorProfilerCallback:: jınkıx](icorprofilercallback-jitinlining-method.md) geri aramasını kullanarak başlangıçta profil oluşturucu tarafından ayarlanan hata ayıklayıcıyı, genel bayrakları içerir.  JıT derleyicisi en az en iyileştirme miktarını isteyen bir kaynağa öncelik verir.  Örneğin, profil oluşturucu `COR_PRF_DISABLE_INLINING` Başlangıçta belirtiyorsa, ancak `COR_PRF_CODEGEN_DISABLE_INLINING` [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) geri çağırma öğesinde belirtilmemişse, hala devre dışı bırakılmıştır.  Benzer şekilde, profil oluşturucu `COR_PRF_CODEGEN_DISABLE_INLINING` içinde belirtilmemişse `SetCodegenFlags` , ancak [ICorProfilerCallback:: jıntıl](icorprofilercallback-jitinlining-method.md) geri aramasını kullanarak içe/veya devre dışı bırakır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionControl Arabirimi](icorprofilerfunctioncontrol-interface.md)
