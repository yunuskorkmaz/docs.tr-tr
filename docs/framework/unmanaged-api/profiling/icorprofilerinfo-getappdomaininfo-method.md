---
title: ICorProfilerInfo::GetAppDomainInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864121"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo Yöntemi
Bir uygulama etki alanı KIMLIĞINI kabul eder. Bir uygulama etki alanı adı ve onu içeren işlemin KIMLIĞINI döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `appDomainId`  
 'ndaki Uygulama etki alanının KIMLIĞI.  
  
 `cchName`  
 'ndaki `szName` dönüş arabelleğinin karakter cinsinden uzunluğu.  
  
 `pcchName`  
 dışı Uygulama etki alanı adının toplam karakter uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Arayan tarafından sunulan geniş bir karakter arabelleği. Yöntemi döndürüldüğünde, `szName` tam veya kısmi uygulama etki alanı adını içerecektir.  
  
 `pProcessId`  
 dışı Uygulama etki alanını içeren işlemin KIMLIĞINE yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem çağrıldıktan sonra, `szName` arabelleğinin uygulama etki alanının tam adını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın. `pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetAppDomainInfo` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetAppDomainInfo` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcchName` döndürülen değere ayarlayabilir ve `GetAppDomainInfo` tekrar çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
