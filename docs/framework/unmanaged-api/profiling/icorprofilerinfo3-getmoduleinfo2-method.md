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
ms.openlocfilehash: e2a4df262e076c960640977bea0d22be19802140
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449676"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 Metodu
Modül KIMLIĞI verildiğinde, modülün dosya adını, modülün üst derleme KIMLIĞINI ve modülün özelliklerini açıklayan bir bit maskesini döndürür.  
  
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
 'ndaki Bilgilerin alınacağı modülün KIMLIĞI.  
  
 `ppBaseLoadAddress`  
 dışı Modülün yüklendiği temel adres.  
  
 `cchName`  
 'ndaki `szName` dönüş arabelleğinin karakter cinsinden uzunluğu.  
  
 `pcchName`  
 dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Arayan tarafından sunulan geniş bir karakter arabelleği. Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.  
  
 `pAssemblyId`  
 dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.  
  
 `pdwModuleFlags`  
 dışı [Cor_prf_module_flags](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) Numaralandırmadaki, modülün özelliklerini belirten değerlerin bir bit maskesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için `szName` parametresi modülün meta veri adıdır ve temel adres 0 (sıfır) olur. Meta veri adı, meta veriler içindeki modül tablosundan Ad sütunundaki değerdir. Bu Ayrıca, yönetilen koda <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> özelliği olarak ve [IMetaDataImport:: GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) yönteminin `szName` parametresi olarak yönetilmeyen meta veri istemci koduna da sunulur.  
  
 `GetModuleInfo2` yöntemi modülün KIMLIĞI mevcut olduğu anda çağrılabilir olsa da, ana derlemenin KIMLIĞI, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.  
  
 `GetModuleInfo2` döndüğünde, `szName` arabelleğinin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın. `pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetModuleInfo2` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetModuleInfo2` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcchName` döndürülen değere ayarlayabilir ve `GetModuleInfo2` tekrar çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
