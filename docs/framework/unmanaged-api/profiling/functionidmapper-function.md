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
ms.openlocfilehash: afc818dfe625bfc329ceb1660539eb119702a90d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500682"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper İşlevi
Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. `FunctionIDMapper`Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[' de] yeniden eşleştirilecek işlev tanımlayıcısı.

- `pbHookFunction`

  \[out] profil oluşturucunun `true` ,, ve geri çağırmaları almak istiyorsa bir değere yönelik bir işaretçi `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` ; Aksi takdirde, bu değeri olarak ayarlar `false` .

## <a name="return-value"></a>Dönüş Değeri  
 Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür. Dönüş değeri, `false` içinde döndürülmediği takdirde null olamaz `pbHookFunction` . Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi çok büyük olasılıkla halele vermez.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionIDMapper`İşlev bir geri çağırma. Bir işlev KIMLIĞINI profil Oluşturucu için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profil oluşturucu tarafından uygulanır. , `FunctionIDMapper` Verilen herhangi bir işlev için kullanılacak ALTERNATIF kimliği döndürür. Yürütme altyapısı daha sonra bu alternatif KIMLIĞI geçirerek (geleneksel işlev KIMLIĞINE ek olarak,, `clientData` `FunctionEnter2` `FunctionLeave2` , ve `FunctionTailcall2` kancalarının çağrıldığı işlevi belirlemek için),, ve kancalarının parametresindeki profil oluşturucuya geri dönerek profil oluşturucunun isteğine geçer.  
  
 İşlevin uygulamasını belirtmek için [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz `FunctionIDMapper` . `ICorProfilerInfo::SetFunctionIDMapper`Yöntemi yalnızca bir kez çağırabilir ve [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırmasında bunu yapmanızı öneririz.  
  
 Varsayılan olarak, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağını ayarlayan ve [ICorProfilerInfo:: Setenterleavefunctionkancaları](icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)aracılığıyla kancaları ayarlayan bir profil oluşturucu, `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` her işlev için, ve geri çağırmaları almalıdır. Ancak, profil oluşturucular ' `FunctionIDMapper` ye ayarlayarak belirli işlevler için bu geri çağırmaları, seçmeli olarak almak için uygulanabilir `pbHookFunction` `false` .  
  
 Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı anda aynı yöntemi/işlevi aldığı durumlarda toleranslı olmalıdır. Bu gibi durumlarda, profil oluşturucu `FunctionIDMapper` aynı için birden fazla geri çağırma alabilir `FunctionID` . Profil Oluşturucu aynı değeri aynı değer ile birden çok kez çağrıldığında, bu geri aramadan aynı değerleri döndürmelidir `FunctionID` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetFunctionIDMapper Yöntemi](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 İşlevi](functionidmapper2-function.md)
- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [FunctionTailcall2 İşlevi](functiontailcall2-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
