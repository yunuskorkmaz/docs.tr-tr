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
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496145"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 Metodu
Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionID`  
 'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.  
  
 `reJitId`  
 'ndaki JıT-yeniden derleme işlevinin kimliği.  
  
 `cCodeInfos`  
 'ndaki `codeInfos`Dizinin boyutu.  
  
 `pcCodeInfos`  
 dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.  
  
 `codeInfos`  
 dışı Arayan tarafından sağlanmış arabellek. Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetCodeInfo3`Yöntemi, [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)ile benzerdir, ancak belirtilen IP ADRESINI içeren işlevin JıT yeniden derlenmesi kimliğini alır.  
  
> [!NOTE]
> `GetCodeInfo3`bir çöp toplama tetiklenebilir, ancak [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) olmayacaktır. Daha fazla bilgi için bkz. HRESULT [corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md) .  
  
 Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.  
  
 `GetCodeInfo3`Geri döndüğünde, `codeInfos` arabelleğin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` . `cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuna göre ayrılmışsa `pcCodeInfos` , daha büyük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo3` yeniden çağırın.  
  
 Alternatif olarak, `GetCodeInfo3` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo3` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeInfo2 Yöntemi](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
