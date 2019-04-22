---
title: ICorProfilerInfo::GetModuleInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69db53c03d68e30507ff3ab2b11b663970d59af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090816"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo Yöntemi
Bir modül kimliği söz konusu modülün dosya adı ve modülün üst derleme Kimliğini döndürür.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Bilgileri alınır modül kimliği.  
  
 `ppBaseLoadAddress`  
 [out] Modülün yüklendiği temel adres.  
  
 `cchName`  
 [in] Karakter cinsinden uzunluğu, `szName` dönüş arabelleği.  
  
 `pcchName`  
 [out] Bir işaretçi döndürülür modülün dosya adının toplam karakter uzunluğu.  
  
 `szName`  
 [out] Bir çağıran tarafından sağlanan geniş karakter arabelleği. Yöntem döndürüldüğünde bu arabellek modülü dosya adını içerir.  
  
 `pAssemblyId`  
 [out] Modülün üst derleme kimliği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için `szName` parametresi boş bir dize ve 0 (sıfır) taban adresidir.  
  
 Ancak `GetModuleInfo` yöntemi çağrıldığında modülün kimliği var. hemen sonra Profil Oluşturucu alıncaya kadar üst derlemesinin kimliği kullanılabilir olmayacak [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.  
  
 Zaman `GetModuleInfo` döndürür, doğrulamalısınız `szName` arabellek modülün tam dosya adını içerecek şekilde büyük. Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetModuleInfo` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetModuleInfo` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
