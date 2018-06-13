---
title: ICorProfilerInfo4::GetCodeInfo3 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cebf5f1101abed29bc325cec2390b4fd13056e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459976"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 Metodu
Belirtilen işlev JIT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsam alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionID`  
 [in] Yerel kod ilişkilendirildiği işlevi kimliği.  
  
 `reJitId`  
 [in] JIT yeniden derlenmesi işlevi kimliği.  
  
 `cCodeInfos`  
 [in] Boyutunu `codeInfos` dizi.  
  
 `pcCodeInfos`  
 [out] Toplam sayısını gösteren bir işaretçi [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları kullanılabilir.  
  
 `codeInfos`  
 [out] Çağıran tarafından sağlanan arabellek. Metodu döndükten sonra bir dizi içerir `COR_PRF_CODE_INFO` yapıları, yerel kod bloğunu her biri açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetCodeInfo3` Yöntemi benzer [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)dışında belirtilen IP adresi içeren işlevi JIT yeniden derlenmesi Kimliğini alır.  
  
> [!NOTE]
>  `GetCodeInfo3` Çöp toplama, ancak tetikleyebilir [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) almayacak. Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Kapsam, ortak Ara dili (CIL) uzaklığı artan düzende sıralanır.  
  
 Sonra `GetCodeInfo3` döndürür, doğrulamalısınız `codeInfos` arabellek tüm içerecek şekilde büyük [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapıları. Bunu yapmak için değeri ile karşılaştırın `cCodeInfos` değeriyle `cchName` parametresi. Varsa `cCodeInfos` boyutu tarafından ayrılmış bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısıdır küçüktür `pcCodeInfos`, daha geniş bir ayırma `codeInfos` arabellek, güncelleştirme `cCodeInfos` yeni, büyük boyutu ve arama `GetCodeInfo3` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetCodeInfo3` sıfır uzunluklu ile `codeInfos` arabellek doğru arabellek boyutu elde edilir. Ardından ayarlayabilirsiniz `codeInfos` arabellek boyutu için döndürülen değer `pcCodeInfos`, boyutuna çarpılan bir [cor_prf_code_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı ve çağrı `GetCodeInfo3` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetCodeInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
