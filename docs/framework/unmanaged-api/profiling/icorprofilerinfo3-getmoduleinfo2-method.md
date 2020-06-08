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
ms.openlocfilehash: d2b7e93866bf0aa79849925234a4d6e4cc9b5b52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502827"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 Metodu
Modül KIMLIĞI verildiğinde, modülün dosya adını, modülün üst derleme KIMLIĞINI ve modülün özelliklerini açıklayan bir bit maskesini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Dönüş arabelleğinin karakter cinsinden uzunluğu `szName` .  
  
 `pcchName`  
 dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Arayan tarafından sunulan geniş bir karakter arabelleği. Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.  
  
 `pAssemblyId`  
 dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.  
  
 `pdwModuleFlags`  
 dışı [Cor_prf_module_flags](cor-prf-module-flags-enumeration.md) Numaralandırmadaki, modülün özelliklerini belirten değerlerin bir bit maskesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için parametresi, `szName` modülün meta veri adıdır ve temel adres 0 (sıfır) olur. Meta veri adı, meta veriler içindeki modül tablosundan Ad sütunundaki değerdir. Bu, <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> yönetilen koda özellik olarak ve `szName` [IMetaDataImport:: GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) yönteminin parametresi olarak yönetilmeyen meta veri istemci koduna olarak da sunulur.  
  
 `GetModuleInfo2`Yöntemi modülün kimliği mevcut olduğu anda çağrılabilir olsa da, ana DERLEMENIN kimliği, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.  
  
 `GetModuleInfo2`' İ döndüğünde, `szName` arabelleğin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` . Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetModuleInfo2` yeniden çağırın.  
  
 Alternatif olarak, `GetModuleInfo2` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetModuleInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
