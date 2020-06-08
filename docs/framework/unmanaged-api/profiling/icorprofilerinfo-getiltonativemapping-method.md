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
ms.openlocfilehash: b3c0bee44bf49c7966b8fefcfe6460c6255375c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502996"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping Metodu
Microsoft ara dili (MSIL) uzaklıklarından, belirtilen işlevde bulunan kodun yerel uzaklıklarından bir harita alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Dizinin en büyük boyutu `map` .  
  
 `pcMap`  
 dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.  
  
 `map`  
 dışı `COR_DEBUG_IL_TO_NATIVE_MAP`Her biri uzaklıkları belirten yapıların dizisi. `GetILToNativeMapping`Yöntem döndüğünde, `map` yapıların bazılarını veya tümünü içerir `COR_DEBUG_IL_TO_NATIVE_MAP` .  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping`Yöntemi bir yapı dizisini döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` . Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.  
  
 `GetILToNativeMapping`Geri döndüğünde, `map` arabelleğin tüm yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir `COR_DEBUG_IL_TO_NATIVE_MAP` . Bunu yapmak için değerini `cMap` parametresinin değeriyle karşılaştırın `pcMap` . `pcMap`Değer, bir yapının boyutuyla çarpıldığı zaman, daha büyüktür `COR_DEBUG_IL_TO_NATIVE_MAP` `cMap` , daha büyük bir `map` arabellek ayırır, `cMap` Yeni, daha büyük boyutla güncelleştirin ve `GetILToNativeMapping` yeniden çağırın.  
  
 Alternatif olarak, `GetILToNativeMapping` `map` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcMap` ve `GetILToNativeMapping` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [GetILToNativeMapping2 Yöntemi](icorprofilerinfo4-getiltonativemapping2-method.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
