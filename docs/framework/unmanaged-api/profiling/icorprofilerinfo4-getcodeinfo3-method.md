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
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912709"
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
 'ndaki `codeInfos` Dizinin boyutu.  
  
 `pcCodeInfos`  
 dışı Kullanılabilir toplam [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı sayısına yönelik bir işaretçi.  
  
 `codeInfos`  
 dışı Arayan tarafından sağlanmış arabellek. Yöntem çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` bir yapı dizisi içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi, GetCodeInfo2 ile benzerdir, ancak belirtilen IP adresini içeren işlevin JIT yeniden derlenmesi kimliğini alır. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) `GetCodeInfo3`  
  
> [!NOTE]
> `GetCodeInfo3`bir çöp toplama tetiklenebilir, ancak [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) olmayacaktır. Daha fazla bilgi için bkz. [corprof_e_unsupported_call_sequence](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.  
  
 Geri döndüğünde, `codeInfos` arabelleğin tüm COR_PRF_CODE_INFO yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo3` Bunu yapmak için değerini `cCodeInfos` `cchName` parametresinin değeriyle karşılaştırın. `codeInfos` `cCodeInfos` `GetCodeInfo3` [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) BirCOR_PRF_CODE_INFO`pcCodeInfos`yapısının boyutuna göre ayrılmışsa,dahaküçükbirarabellekayırarak,yeni,dahabüyükboyutlagüncelleştirin`cCodeInfos` ve yeniden çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu `GetCodeInfo3` elde etmek için ilk olarak `codeInfos` sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu ' de `pcCodeInfos`döndürülen değere ayarlayabilir, bir COR_PRF_CODE_INFO yapısının boyutuyla çarpılır ve yeniden çağırabilirsiniz. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo3`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
