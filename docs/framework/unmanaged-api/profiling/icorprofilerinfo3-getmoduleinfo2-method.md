---
title: ICorProfilerInfo3::GetModuleInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetModuleInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b891f55ab79d32814f44eabf50343aa113b0835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 Metodu
Modül kimliği derleme ve modül özelliklerini açıklayan bir bit maskesi modül, modülün üst Kimliğini dosya adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
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
  
 `pdwModuleFlags`  
 [out] Bir bit maskesi değerleri [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) modülü özelliklerini belirtin numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modülleri için `szName` parametresi modülün meta veri adı ve temel adres 0 (sıfır). Meta verileri, meta veri içindeki modül tablosundan adı sütunundaki değeri adıdır. Bu ayrıca olarak sunulan <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği yönetilen kod için ve olarak `szName` parametresinin [Imetadataımport::getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yönetilmeyen meta veriler istemci kodu yöntemi.  
  
 Ancak `GetModuleInfo2` modülün kimliği var hemen yöntemi'nin çağrılabilir, profil oluşturucu alıncaya kadar üst derleme Kimliğini kullanılamaz [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.  
  
 Zaman `GetModuleInfo2` döndürür, doğrulamalısınız `szName` arabellek modülü tam dosya adını içerecek kadar büyük. Bunu yapmak için değeri karşılaştırın, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret eden daha büyük bir değere `cchName`, daha geniş bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, büyük boyutu ve çağrı `GetModuleInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo2` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcchName` ve arama `GetModuleInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
