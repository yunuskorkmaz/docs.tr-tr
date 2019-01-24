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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d65d918147423396a18d2ea5c3edf7ff60c26a11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556135"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper İşlevi
Profil Oluşturucu bir işlev, verilen tanımlayıcıya için kullanılmak üzere diğer Kimliğe yeniden eşlenebileceğini bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) söz konusu işlev için geri çağırmaları. `FunctionIDMapper` Ayrıca, profil oluşturucunun söz konusu işlev için geri çağırmaları almak isteyip istemediğini göstermesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Eşleştirilecek işlev tanımlayıcı.  
  
 `pbHookFunction`  
 [out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` geri çağırmaları; Aksi takdirde, bu değeri ayarlar `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Profil Oluşturucu, yürütme altyapısı bir alternatif bir işlev tanımlayıcı olarak kullanan bir değer döndürür. Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`. Aksi takdirde, null dönüş değeri, büyük olasılıkla işlem durdurma dahil, öngörülemeyen sonuçlara üretecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionIDMapper` Bir geri çağırma işlevidir. Bir işlev kimliği için profil oluşturucuyu daha yararlı olan bazı bir tanımlayıcıya yeniden eşlemek için Profil Oluşturucu tarafından uygulanır. `FunctionIDMapper` Belirli bir işlev için kullanılacak alternatif Kimliğini döndürür. Ardından yürütme altyapısı profil geri dön geleneksel işlevi kimliği yanı sıra bu alternatif kimliği geçirerek profil oluşturucunun isteği geliştirir `clientData` parametresinin `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` kancaları tanımlamak için kanca hangi Aranan işlev.  
  
 Kullanabileceğiniz [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) uygulamasını belirtmek üzere yöntem `FunctionIDMapper` işlevi. Çağırabilirsiniz `ICorProfilerInfo::SetFunctionIDMapper` yöntemi yalnızca bir kez ve biz öneririz, böylece bunu [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.  
  
 Varsayılan olarak, bir profil oluşturucu, COR_PRF_MONITOR_ENTERLEAVE bayrağını kullanarak ayarlar, görünür duruma varsayılır [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), ve kancaları aracılığıyla ayarlar [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [Icorprofilerınfo2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), alması gereken `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` her işlev için geri çağırmaları. Ancak, profil oluşturucular uygulayabilir `FunctionIDMapper` ayarlayarak bu geri aramalarda belirli alma seçici olarak önlemek için işlevleri `pbHookFunction` için `false`.  
  
 Profil oluşturucular burada birden çok iş parçacığı profili oluşturulan bir uygulamanın aynı yöntemi/işlevi aynı anda aradığınız örneklerini dayanıklı olması gerekir. Böyle durumlarda, birden çok profil oluşturucu alabilirsiniz `FunctionIDMapper` geri çağırmalar için aynı `FunctionID`. Profil Oluşturucu ile aynı birden çok kez çağrıldığında, bu geri çağrısından aynı değerleri döndürülecek belirli olmalıdır `FunctionID`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [SetFunctionIDMapper Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
