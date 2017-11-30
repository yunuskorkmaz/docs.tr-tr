---
title: ICorProfilerInfo::GetAppDomainInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo Metodu
Bir uygulama etki alanı kimliği kabul eder Uygulama etki alanı adını ve içerdiği işlem Kimliğini döndürür.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `appDomainId`  
 [in] Uygulama etki alanı kimliği.  
  
 `cchName`  
 [in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.  
  
 `pcchName`  
 [out] Uygulama etki alanı adının toplam karakter uzunluğu için bir işaretçi.  
  
 `szName`  
 [out] Çağıran tarafından sağlanan geniş karakter arabellek. Yöntem döndüğünde `szName` tam veya kısmi uygulama etki alanı adını içerir.  
  
 `pProcessId`  
 [out] Uygulama etki alanını içeren işlem kimliği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem döndükten sonra doğrulamanız gerekir `szName` arabellek uygulama etki alanının tam adını içerecek kadar büyük. Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetAppDomainInfo` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetAppDomainInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetAppDomainInfo` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
