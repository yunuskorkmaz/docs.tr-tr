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
ms.openlocfilehash: 164e042ab0f1a275ff07b917658024e22c2d7b0b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862042"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 Metodu
Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `codeInfos` dizisinin boyutu.  
  
 `pcCodeInfos`  
 dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.  
  
 `codeInfos`  
 dışı Arayan tarafından sağlanmış arabellek. Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetCodeInfo3` yöntemi [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)ile benzerdir, ancak belirtilen IP adresini IÇEREN işlevin JIT YENIDEN derlenmesi kimliğini alır.  
  
> [!NOTE]
> `GetCodeInfo3` bir çöp toplamayı tetikleyebilir, ancak [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) olmayacaktır. Daha fazla bilgi için bkz. HRESULT [corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md) .  
  
 Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.  
  
 `GetCodeInfo3` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın. [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo3` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo3` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo3` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeInfo2 Yöntemi](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
