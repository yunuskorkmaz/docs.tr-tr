---
title: ICorProfilerInfo::GetModuleInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 23dc0208b4537530f18c2c282fbe8c3495ba301f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo Metodu
Modül kimliği modülün dosya adı ve modülün üst derleme Kimliğini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Bilgiler alınır modül kimliği.  
  
 `ppBaseLoadAddress`  
 [out] Modül yüklendiği temel adres.  
  
 `cchName`  
 [in] Karakter cinsinden uzunluğu, `szName` dönüş arabellek.  
  
 `pcchName`  
 [out] Toplam karakter uzunluğu döndürülen modülün dosya adı için bir işaretçi.  
  
 `szName`  
 [out] Çağıran tarafından sağlanan geniş karakter arabellek. Yöntem döndüğünde, bu arabellek modülü dosya adını içerir.  
  
 `pAssemblyId`  
 [out] Modülün üst derleme kimliği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modülleri için `szName` parametresi boş bir dize ve taban adresi 0 (sıfır).  
  
 Ancak `GetModuleInfo` modülün kimliği var hemen yöntemi'nin çağrılabilir, profil oluşturucu alıncaya kadar üst derleme Kimliğini kullanılamaz [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.  
  
 Zaman `GetModuleInfo` döndürür, doğrulamalısınız `szName` arabellek modülü tam dosya adını içerecek kadar büyük. Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetModuleInfo` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetModuleInfo` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [Getmoduleınfo2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
