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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ffdb04bdf3fd2f605e2dffc5065a0d786bbaf7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967913"
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
 'ndaki `map` Dizinin en büyük boyutu.  
  
 `pcMap`  
 dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.  
  
 `map`  
 dışı Her biri uzaklıkları belirten `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların dizisi. Yöntem döndüğünde, `map` yapıların`COR_DEBUG_IL_TO_NATIVE_MAP` bazılarını veya tümünü içerir. `GetILToNativeMapping2`  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping2`, [ICorProfilerInfo:: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) yöntemine benzerdir, ancak profil oluşturucunun gelecek sürümlerde yeniden derlenen işlevin kimliğini belirtmesini sağlar.  
  
> [!NOTE]
> [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi, .NET Framework 4,5 ' de uygulanmıyor, bu nedenle JIT yeniden derlenecek olan işlevlerin ilk derlenmiş işlevden farklı bir IL-yerel eşlemesi olamaz. Bu nedenle, `GetILToNativeMapping2` .NET Framework 4,5 ' de sıfır olmayan bir JIT kimliği ile çağrılamaz.  
  
 Yöntemi bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapı dizisini döndürür. `GetILToNativeMapping2` Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.  
  
 Geri döndüğünde, `map` arabelleğin tüm `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir. `GetILToNativeMapping2` Bunu yapmak için değerini `cMap` `pcMap` parametresinin değeriyle karşılaştırın. `COR_DEBUG_IL_TO_NATIVE_MAP` `GetILToNativeMapping2` `cMap` `map` Değer, bir`cMap`yapının boyutuyla çarpıldığı zaman, daha büyüktür, daha büyük bir arabellek ayırır, yeni, daha büyük boyutla güncelleştirin ve `pcMap` yeniden çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu `GetILToNativeMapping2` elde etmek için ilk olarak `map` sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra arabellek boyutunu içinde `pcMap` döndürülen değere ayarlayabilir ve yeniden çağırabilirsiniz. `GetILToNativeMapping2`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
