---
title: ICorProfilerInfo4::GetILToNativeMapping2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetILToNativeMapping2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d5ce076ad66214f786f7e221a0443edf7986c5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 Metodu
Belirtilen işlev JIT yeniden derlenmesi sürümünde yer alan kodu için yerel uzaklık için Ara dili (MSIL) kaydırır Microsoft'tan bir harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kod içeren işlevi kimliği.  
  
 `pReJitId`  
 [in] JIT yeniden derlenmesi işlevi kimliği. Kimliği sıfır olmalıdır [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `cMap`  
 [in] En büyük boyutunu `map` dizi.  
  
 `pcMap`  
 [out] Kullanılabilir cor_debug_ıl_to_natıve_map yapıları toplam sayısı.  
  
 `map`  
 [out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları, her biri uzaklıkları belirtir. Sonra `GetILToNativeMapping2` yöntemi döndürür `map` bazılarını veya tümünü içerecek `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping2`benzer [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) derlenmiş işlevi kimliği gelecekte belirtmek profil oluşturucu izin verir ancak bu yöntem, serbest bırakır.  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi uygulanan değil [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]JIT yeniden derlenmesi işlevler farklı bir IL yerel eşlemesi olamaz nedenle ilk olarak derlenmiş işlevi. Bu nedenle, `GetILToNativeMapping2` sıfır olmayan bir JIT yeniden derlenmesi kimliği ile çağrılamaz [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `GetILToNativeMapping2` Yöntemi bir dizi döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları. Belirli yerel yönergeler aralıklarını kod (örneğin, giriş) özel bölgeler için karşılık gelen iletmek için dizi bir girişe sahip olabilir, `ilOffset` alan için bir değer kümesi [Cordebugıltonativemappingtypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) sabit listesi.  
  
 Sonra `GetILToNativeMapping2` döndürür, doğrulamalısınız `map` arabellek tüm içerecek şekilde büyük `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları. Bunu yapmak için değeri ile karşılaştırın `cMap` değeriyle `pcMap` parametresi. Varsa `pcMap` boyutuyla çarpılır olduğunda değeri bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısı, büyük `cMap`, daha geniş bir ayırma `map` arabellek, güncelleştirme `cMap` yeni, büyük boyutu ve çağrı `GetILToNativeMapping2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetILToNativeMapping2` sıfır uzunluklu ile `map` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcMap` ve arama `GetILToNativeMapping2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
