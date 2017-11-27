---
title: ICorProfilerInfo::GetAssemblyInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4eab4a4bfbf91fd86a3742600f3383a8d374905
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo Metodu
Bir derleme kimliği kabul eder ve derlemenin adını ve kendi bildirim modülünden Kimliğini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `assemblyId`  
 [in] Derleme tanımlayıcısı.  
  
 `cchName`  
 [in] Karakter cinsinden uzunluğu, `szName`.  
  
 `pcchName`  
 [out] Derlemenin adı toplam karakter uzunluğu için bir işaretçi.  
  
 `szName`  
 [out] Çağıran tarafından sağlanan geniş karakter arabellek. İşlevi döndüğünde, derleme adı içerir.  
  
 `pAppDomainId`  
 [out] Derleme içeren uygulama etki alanı kimliği için bir işaretçi.  
  
 `pModuleId`  
 [out] Derleme bildirimi modülünün kimliği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem döndükten sonra doğrulamanız gerekir `szName` arabellek derlemenin tam adını içerecek kadar büyük. Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetAssemblyInfo` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetAssemblyInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Ardından, döndürülen değer göre arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetAssemblyInfo` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
