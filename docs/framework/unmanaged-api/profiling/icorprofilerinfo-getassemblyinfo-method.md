---
title: ICorProfilerInfo::GetAssemblyInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 41083b2fcd61a9a726e835c3d5710308aa634600
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498654"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo Metodu
Bir derleme KIMLIĞI kabul eder ve derlemenin adını ve bildirim modülünün KIMLIĞINI döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `assemblyId`  
 'ndaki Derlemenin tanımlayıcısı.  
  
 `cchName`  
 'ndaki Karakter cinsinden uzunluğu `szName` .  
  
 `pcchName`  
 dışı Derlemenin adının toplam karakter uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Arayan tarafından sunulan geniş bir karakter arabelleği. İşlev döndüğünde, derlemenin adını içerir.  
  
 `pAppDomainId`  
 dışı Derlemeyi içeren uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.  
  
 `pModuleId`  
 dışı Derlemenin bildirim modülünün KIMLIĞINE yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem çağrıldıktan sonra, `szName` arabelleğin tam adı içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` . Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetAssemblyInfo` yeniden çağırın.  
  
 Alternatif olarak, `GetAssemblyInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra, içinde döndürülen değere göre arabellek boyutunu ayarlayabilir `pcchName` ve `GetAssemblyInfo` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
