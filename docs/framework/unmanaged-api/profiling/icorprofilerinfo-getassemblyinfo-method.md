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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3579020ce268cd59a091e685fae2e97b3191c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
