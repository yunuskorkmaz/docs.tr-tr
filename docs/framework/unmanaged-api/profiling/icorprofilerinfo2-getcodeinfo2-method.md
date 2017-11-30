---
title: ICorProfilerInfo2::GetCodeInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetCodeInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c2526c286e4014b32e63ec34f9d212a5f657756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 Metodu
Yerel kod belirtilen ile ilişkili kapsam alır `FunctionID`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionID`  
 [in] Yerel kod ilişkilendirildiği işlevi kimliği.  
  
 `cCodeInfos`  
 [in] Boyutunu `codeInfos` dizi.  
  
 `pcCodeInfos`  
 [out] Toplam sayısını gösteren bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.  
  
 `codeInfos`  
 [out] Çağıran tarafından sağlanan arabellek. Metodu döndükten sonra bir dizi içerir `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunu her biri açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsam artan Microsoft Ara dili (MSIL) uzaklığı düzende sıralanır.  
  
 Sonra `GetCodeInfo2` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük `COR_PRF_CODE_INFO` yapıları. Bunu yapmak için değeri ile karşılaştırın `cCodeInfos` değeriyle `cchName` parametresi. Varsa `cCodeInfos` boyutu tarafından ayrılmış bir `COR_PRF_CODE_INFO` yapısıdır küçüktür `pcCodeInfos`, daha geniş bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, büyük boyutu ve çağrı `GetCodeInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo2` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir. Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu için döndürülen değer `pcCodeInfos`, boyutuna çarpılan bir `COR_PRF_CODE_INFO` yapısı ve çağrı `GetCodeInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Getcodeınfo3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [Icorprofilerınfo2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
