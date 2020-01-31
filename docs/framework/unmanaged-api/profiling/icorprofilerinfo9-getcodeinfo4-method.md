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
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868310"
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

## <a name="parameters"></a>Parametreler

- `pNativeCodeStartAddress`

  \[, yerel bir işlevin başlangıcına yönelik bir işaretçidir.

- `cCodeInfos`

  `codeInfos` dizisinin boyutu \[.

- `pcCodeInfos`

  \[out] kullanılabilen toplam [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısı sayısına yönelik bir işaretçi.

- `codeInfos`

  \[out] arayan tarafından sağlanmış bir arabellek. Yöntemi çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` yapıları dizisi içerir.

## <a name="remarks"></a>Açıklamalar

`GetCodeInfo4` yöntemi [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)ile benzerdir, ancak yöntemin farklı yerel sürümleri için kod bilgilerini arayabilir.

> [!NOTE]
> `GetCodeInfo4` bir çöp toplama tetikleyebilirler.

Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.

`GetCodeInfo4` çağrıldıktan sonra, `codeInfos` arabelleğinin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `cCodeInfos` değerini `cchName` parametresinin değeri ile karşılaştırın. [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısına bölünen `cCodeInfos`, `pcCodeInfos`daha küçüktür, daha büyük bir `codeInfos` arabelleği ayırın, yeni, daha büyük boyutlu `cCodeInfos` güncelleştirin ve `GetCodeInfo4` çağırın.

Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetCodeInfo4` sıfır uzunluklu `codeInfos` arabelleği ile çağırabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu `pcCodeInfos`döndürülen değere ayarlayabilirsiniz, bir [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo4` yeniden çağırabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 arabirimi](ICorProfilerInfo9-interface.md)
