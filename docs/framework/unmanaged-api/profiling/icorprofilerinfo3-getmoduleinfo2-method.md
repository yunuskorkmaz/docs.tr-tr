---
title: ICorProfilerInfo3::GetModuleInfo2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ead38d54d470c3f443ae5e27e4a2d045bc27c79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783029"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 Metodu
Derleme ve modül özelliklerini açıklayan bir bit maskesi, bir modül kimliği modül, modülün üst kimliği dosya adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
 `pdwModuleFlags`  
 [out] Bir bit maskesi değerleri [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) modülü özelliklerini belirten sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için `szName` modülü meta veri adı bir parametredir ve 0 (sıfır) taban adresidir. Meta veri değeri meta verileri içinde modül tablosundaki Ad sütununda addır. Bu ayrıca olarak gösterilir <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği yönetilen koda ve olarak `szName` parametresinin [Imetadataımport::getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yöntemi yönetilmeyen meta veriler istemci kodu.  
  
 Ancak `GetModuleInfo2` yöntemi çağrıldığında modülün kimliği var. hemen sonra Profil Oluşturucu alıncaya kadar üst derlemesinin kimliği kullanılabilir olmayacak [Icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırma.  
  
 Zaman `GetModuleInfo2` döndürür, doğrulamalısınız `szName` arabellek modülün tam dosya adını içerecek şekilde büyük. Bunu yapmak için değeri ile karşılaştırmak, `pcchName` değeriyle işaret `cchName` parametresi. Varsa `pcchName` işaret değerinden daha büyük bir değere `cchName`, daha büyük bir ayırma `szName` arabellek, güncelleştirme `cchName` yeni, daha büyük bir boyut ve çağrı `GetModuleInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetModuleInfo2` sıfır uzunluklu ile `szName` arabellek doğru arabellek boyutu elde edilir. Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcchName` ve çağrı `GetModuleInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
