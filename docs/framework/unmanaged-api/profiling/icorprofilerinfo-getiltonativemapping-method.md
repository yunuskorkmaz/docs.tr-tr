---
title: ICorProfilerInfo::GetILToNativeMapping Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89ccfcbf69a0d3907ec244d7a214d6f4a5766767
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping Metodu
Belirtilen işlevinde kod için yerel uzaklık için Ara dili (MSIL) kaydırır Microsoft'tan bir harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kod içeren işlevi kimliği.  
  
 `cMap`  
 [in] En büyük boyutunu `map` dizi.  
  
 `pcMap`  
 [out] Kullanılabilir cor_debug_ıl_to_natıve_map yapıları toplam sayısı.  
  
 `map`  
 [out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları, her biri uzaklıkları belirtir. Sonra `GetILToNativeMapping` yöntemi döndürür `map` bazılarını veya tümünü içerecek `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping` Yöntemi bir dizi döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları. Belirli yerel yönergeler aralıklarını kod (örneğin, giriş) özel bölgeler için karşılık gelen iletmek için dizi bir girişe sahip olabilir, `ilOffset` alan için bir değer kümesi [Cordebugıltonativemappingtypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) sabit listesi.  
  
 Sonra `GetILToNativeMapping` döndürür, doğrulamalısınız `map` arabellek tüm içerecek şekilde büyük `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları. Bunu yapmak için değeri ile karşılaştırın `cMap` değeriyle `pcMap` parametresi. Varsa `pcMap` boyutuyla çarpılır olduğunda değeri bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısı, büyük `cMap`, daha geniş bir ayırma `map` arabellek, güncelleştirme `cMap` yeni, büyük boyutu ve çağrı `GetILToNativeMapping` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetILToNativeMapping` sıfır uzunluklu ile `map` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcMap` ve arama `GetILToNativeMapping` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [GetILToNativeMapping2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
