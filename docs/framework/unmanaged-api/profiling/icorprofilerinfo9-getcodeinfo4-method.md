---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ce29703a181106353695414e8b291b14c697fc56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444792"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4 yöntemi

Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a>Parametreler

`pNativeCodeStartAddress` \
'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.

`cCodeInfos` \
'ndaki `codeInfos` dizisinin boyutu.

`pcCodeInfos` \
dışı [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.

`codeInfos` \
dışı Arayan tarafından sağlanmış arabellek. Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.

## <a name="remarks"></a>Açıklamalar

`GetCodeInfo4` yöntemi [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)ile benzerdir, ancak yöntemin farklı yerel sürümleri için kod bilgilerini arayabilir.

> [!NOTE]
> `GetCodeInfo4` bir çöp toplama tetikleyebilirler.

Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.

`GetCodeInfo4` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın. [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo4` çağırın.

Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo4` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo4` yeniden çağırabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 arabirimi](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
