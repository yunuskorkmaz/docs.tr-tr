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
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502905"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 Yöntemi
Belirtilen yerel kod kapsamlarını alır, bununla ilişkili `FunctionID` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionID`  
 'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.  
  
 `cCodeInfos`  
 'ndaki `codeInfos`Dizinin boyutu.  
  
 `pcCodeInfos`  
 dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.  
  
 `codeInfos`  
 dışı Arayan tarafından sağlanmış arabellek. Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamlar, Microsoft ara dili (MSIL) kaydırmasının artırılması sırasında sıralanır.  
  
 `GetCodeInfo2`Geri döndüğünde, `codeInfos` arabelleğin tüm yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir `COR_PRF_CODE_INFO` . Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` . `cCodeInfos`Bir yapının boyutuna göre ayrılmışsa `COR_PRF_CODE_INFO` `pcCodeInfos` , daha küçük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo2` yeniden çağırın.  
  
 Alternatif olarak, `GetCodeInfo2` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , bir yapının boyutuyla çarpılır `COR_PRF_CODE_INFO` ve `GetCodeInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeInfo3 Yöntemi](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
