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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175180"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper İşlevi
Profiloluşturucuya, bir işlevin verilen tanımlayıcısının [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) aramaları'nda kullanılmak üzere alternatif bir kimlikle yeniden eşlenebileceğini belirtir. `FunctionIDMapper`ayrıca profilleyicinin bu işlev için geri arama almak isteyip istemediğini belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[in] Yeniden alınacak işlev tanımlayıcısı.

- `pbHookFunction`

  \[out] `true` Profiloluşturucunun , `FunctionEnter2`ve `FunctionLeave2` `FunctionTailcall2` geri arama almak istiyorsa ayarladığını bir değere işaretçi; aksi takdirde, bu `false`değeri .

## <a name="return-value"></a>Dönüş Değeri  
 Profil oluşturucu, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değeri döndürür. İade değeri iade edilmedikçe `false` null `pbHookFunction`olamaz. Aksi takdirde, null bir iade değeri, büyük olasılıkla işlemi durdurmak da dahil olmak üzere öngörülemeyen sonuçlar üretecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev `FunctionIDMapper` bir geri aramadır. Bir işlev kimliğini profilci için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profiloluşturucu tarafından uygulanır. Herhangi `FunctionIDMapper` bir işlev için kullanılacak alternatif kimliği döndürür. Yürütme motoru daha sonra bu alternatif kimlik geçirerek profilci isteği onurlandırır, geleneksel işlev kimliğine `clientData` ek olarak, `FunctionEnter2` `FunctionLeave2`geri `FunctionTailcall2` parametre profilci için , ve kanca, kanca çağrıldığı işlevi tanımlamak için.  
  
 `FunctionIDMapper` İşlevin uygulanmasını belirtmek için [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz. Yöntemi yalnızca bir kez arayabilirsiniz ve [bunu ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback'de yapmanızı öneririz. `ICorProfilerInfo::SetFunctionIDMapper`  
  
 Varsayılan olarak, ICorProfilerInfo kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağı ayarlar bir profilci varsayılır::SetEventMask , ve [ICorProfilerInfo üzerinden kanca ayarlar::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `FunctionEnter2`almak gerekir `FunctionLeave2`, ve `FunctionTailcall2` her fonksiyon için geri arama. [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) Ancak, profilciler `FunctionIDMapper` seçici olarak ayarlayarak `pbHookFunction` belirli işlevler için bu `false`geri aramaları almaktan kaçınmak için uygulayabilir.  
  
 Profilciler, profilli bir uygulamanın birden çok iş parçacığının aynı yöntem/işlevi aynı anda aradığı durumlara toleranslı olmalıdır. Bu gibi durumlarda, profil oluşturucu aynı `FunctionIDMapper` `FunctionID`için birden çok geri arama alabilir. Profil oluşturucu, aynı `FunctionID`ile birden çok kez çağrıldığında bu geri arama aynı değerleri döndürmek için emin olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetFunctionIDMapper Yöntemi](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 İşlevi](functionidmapper2-function.md)
- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [FunctionTailcall2 İşlevi](functiontailcall2-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
