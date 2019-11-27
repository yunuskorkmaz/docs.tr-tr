---
title: FunctionIDMapper İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440696"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper İşlevi
Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. `FunctionIDMapper`, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcId`  
 'ndaki Yeniden eşleştirilecek işlev tanımlayıcısı.  
  
 `pbHookFunction`  
 dışı Profil oluşturucunun `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almak istiyorsa `true` için ayarladığı değere yönelik bir işaretçi; Aksi takdirde, bu değeri `false`olarak ayarlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür. `pbHookFunction``false` döndürülmediği takdirde dönüş değeri null olamaz. Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi çok büyük olasılıkla halele vermez.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionIDMapper` işlevi bir geri çağırmasıdır. Bir işlev KIMLIĞINI profil Oluşturucu için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profil oluşturucu tarafından uygulanır. `FunctionIDMapper`, verilen herhangi bir işlev için kullanılacak alternatif KIMLIĞI döndürür. Yürütme altyapısı daha sonra, bu alternatif KIMLIĞI, geleneksel işlev KIMLIĞINE ek olarak, `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` kancalarını `clientData` parametresindeki Profiler 'a geri geçirerek, kancaın çağrıldığı işlevi belirlemek için profil oluşturucunun isteğine geçer.  
  
 `FunctionIDMapper` işlevinin uygulamasını belirtmek için [ICorProfilerInfo:: SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz. `ICorProfilerInfo::SetFunctionIDMapper` yöntemini yalnızca bir kez çağırabilirsiniz ve [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırmasında bunu yapmanızı öneririz.  
  
 Varsayılan olarak, [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağını ayarlayan ve [ICorProfilerInfo:: Setenterleavefunctionkancaları](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)aracılığıyla kancaları ayarlayan bir profil oluşturucu, her işlev için `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almalıdır. Ancak, profil oluşturucular, `false`' e `pbHookFunction` ayarlayarak belirli işlevler için bu geri çağırmaları almayı seçerek `FunctionIDMapper` uygulayabilir.  
  
 Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı anda aynı yöntemi/işlevi aldığı durumlarda toleranslı olmalıdır. Bu gibi durumlarda, profil oluşturucu aynı `FunctionID`birden çok `FunctionIDMapper` geri çağırma alabilir. Profil Oluşturucu aynı `FunctionID`birden çok kez çağrıldığında, bu geri aramadan aynı değerleri döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetFunctionIDMapper Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
