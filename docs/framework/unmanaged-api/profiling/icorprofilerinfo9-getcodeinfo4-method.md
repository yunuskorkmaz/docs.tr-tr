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
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973701"
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
 `pNativeCodeStartAddress`  
 'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.  

 `cCodeInfos`  
 'ndaki `codeInfos` Dizinin boyutu.  
  
 `pcCodeInfos`  
 dışı Kullanılabilir toplam [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) yapısı sayısına yönelik bir işaretçi.  
  
 `codeInfos`  
 dışı Arayan tarafından sağlanmış arabellek. Yöntem çağrıldıktan sonra, her biri yerel kod bloğunu açıklayan `COR_PRF_CODE_INFO` bir yapı dizisi içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi, bir yöntemin farklı yerel sürümleri için kod bilgilerini aramak dışında, GetCodeInfo3 ile benzerdir. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`  
  
> [!NOTE]
>  `GetCodeInfo4`bir çöp toplama tetiklenebilir.
  
 Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.  
  
 Geri döndüğünde, `codeInfos` arabelleğin tüm COR_PRF_CODE_INFO yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo4` Bunu yapmak için değerini `cCodeInfos` `cchName` parametresinin değeriyle karşılaştırın. `codeInfos` `cCodeInfos` `GetCodeInfo4` [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) BirCOR_PRF_CODE_INFO`pcCodeInfos`yapısının boyutuna göre ayrılmışsa,dahaküçükbirarabellekayırarak,yeni,dahabüyükboyutlagüncelleştirin`cCodeInfos` ve yeniden çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu `GetCodeInfo4` elde etmek için ilk olarak `codeInfos` sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu ' de `pcCodeInfos`döndürülen değere ayarlayabilir, bir COR_PRF_CODE_INFO yapısının boyutuyla çarpılır ve yeniden çağırabilirsiniz. [](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `GetCodeInfo4`   
  

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo9 arabirimi](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

