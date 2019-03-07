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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fe1fa99cb7376aae6dffb2a0973955f417b0b8f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494356"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo Yöntemi
Bir uygulama etki alanı kimliği kabul eder Bir uygulama etki alanı adı ve içerdiği işlem Kimliğini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Uygulama etki alanı kimliği.  
  
 `cchName`  
 [in] Karakter cinsinden uzunluğu, `szName` dönüş arabelleği.  
  
 `pcchName`  
 [out] Uygulama etki alanı adının toplam karakter uzunluğu bir işaretçi.  
  
 `szName`  
 [out] Bir çağıran tarafından sağlanan geniş karakter arabelleği. Yöntem döndürüldüğünde `szName` tam veya kısmi uygulama etki alanı adı içerir.  
  
 `pProcessId`  
 [out] Uygulama etki alanını içeren işlem kimliği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin dönüşünün ardından doğrulamanız gerekir `szName` arabelleği, uygulama etki alanının tam adını içerecek şekilde büyük. Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetAppDomainInfo` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetAppDomainInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetAppDomainInfo` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
