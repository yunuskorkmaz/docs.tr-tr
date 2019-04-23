---
title: ICorProfilerInfo2::GetCodeInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1acf77c250b47bb32a83227a427dd3fe4f909a33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122492"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 Yöntemi
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
  
## <a name="parameters"></a>Parametreler  
 `functionID`  
 [in] Yerel kod ilişkilendirildiği işlevi kimliği.  
  
 `cCodeInfos`  
 [in] Boyutu `codeInfos` dizisi.  
  
 `pcCodeInfos`  
 [out] Toplam sayısı için bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.  
  
 `codeInfos`  
 [out] Çağıran tarafından sağlanan arabellek. Yöntemin dönüşünün ardından bir dizi içerdiği `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunun her biri açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamları, Microsoft Ara dili (MSIL) uzaklığı artan sırada sıralanır.  
  
 Sonra `GetCodeInfo2` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük `COR_PRF_CODE_INFO` yapıları. Bunu yapmak için değeri ile karşılaştırmak `cCodeInfos` değeriyle `cchName` parametresi. Varsa `cCodeInfos` boyutu tarafından ayrılmış bir `COR_PRF_CODE_INFO` yapısıdır küçük `pcCodeInfos`, daha büyük bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, daha büyük bir boyut ve çağrı `GetCodeInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo2` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir. Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu döndürülen değere `pcCodeInfos`, boyutuna göre çarpılan bir `COR_PRF_CODE_INFO` yapısı ve çağrı `GetCodeInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
