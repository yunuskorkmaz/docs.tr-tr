---
title: ICorProfilerInfo::GetILToNativeMapping Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: 8dc551b2b1e29aba371e56eecfd981f16b4b1e3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439042"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping Metodu
Microsoft ara dili (MSIL) uzaklıklarından, belirtilen işlevde bulunan kodun yerel uzaklıklarından bir harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Kodu içeren işlevin KIMLIĞI.  
  
 `cMap`  
 'ndaki `map` dizisinin en büyük boyutu.  
  
 `pcMap`  
 dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.  
  
 `map`  
 dışı Her biri uzaklıkları belirten `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları dizisi. `GetILToNativeMapping` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping` yöntemi `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarından oluşan bir dizi döndürür. Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.  
  
 `GetILToNativeMapping` çağrıldıktan sonra, `map` arabelleğinin tüm `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `cMap` değerini `pcMap` parametresinin değeri ile karşılaştırın. `pcMap` değeri, bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısının boyutuyla çarpıldığı zaman, `cMap`daha büyükse, daha büyük bir `map` arabelleği ayırın, yeni, daha büyük boyutlu `cMap` güncelleştirin ve `GetILToNativeMapping` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetILToNativeMapping` sıfır uzunluklu `map` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcMap` döndürülen değere ayarlayabilir ve `GetILToNativeMapping` tekrar çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [GetILToNativeMapping2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
