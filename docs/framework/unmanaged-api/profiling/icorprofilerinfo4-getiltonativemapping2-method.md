---
title: ICorProfilerInfo4::GetILToNativeMapping2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442929"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 Metodu
Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Kodu içeren işlevin KIMLIĞI.  
  
 `pReJitId`  
 'ndaki JıT-yeniden derleme işlevinin kimliği. Kimlik .NET Framework 4,5 ' de sıfır olmalıdır.  
  
 `cMap`  
 'ndaki `map` dizisinin en büyük boyutu.  
  
 `pcMap`  
 dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.  
  
 `map`  
 dışı Her biri uzaklıkları belirten `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları dizisi. `GetILToNativeMapping2` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping2`, [ICorProfilerInfo:: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) yöntemine benzer, ancak profil oluşturucunun sonraki sürümlerde yeniden derlenen işlevin kimliğini belirtmesini sağlayacaktır.  
  
> [!NOTE]
> [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi, .NET Framework 4,5 ' de uygulanmıyor, bu nedenle JIT yeniden derlenecek olan işlevlerin ilk derlenmiş işlevden farklı bir IL-yerel eşlemesi olamaz. Bu nedenle, `GetILToNativeMapping2` .NET Framework 4,5 ' de sıfır olmayan bir JıT KIMLIĞI ile çağrılamaz.  
  
 `GetILToNativeMapping2` yöntemi `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarından oluşan bir dizi döndürür. Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.  
  
 `GetILToNativeMapping2` çağrıldıktan sonra, `map` arabelleğinin tüm `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `cMap` değerini `pcMap` parametresinin değeri ile karşılaştırın. `pcMap` değeri, bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısının boyutuyla çarpıldığı zaman, `cMap`daha büyükse, daha büyük bir `map` arabelleği ayırın, yeni, daha büyük boyutlu `cMap` güncelleştirin ve `GetILToNativeMapping2` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetILToNativeMapping2` sıfır uzunluklu `map` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcMap` döndürülen değere ayarlayabilir ve `GetILToNativeMapping2` tekrar çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
