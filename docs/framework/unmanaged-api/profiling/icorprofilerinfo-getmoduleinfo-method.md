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
ms.openlocfilehash: 751f2ac44e543fed76c7031791bb57d75ed0fd48
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498108"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo Yöntemi
Bir modül KIMLIĞI verildiğinde, modülün dosya adını ve modülün üst derleme KIMLIĞINI döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için `szName` parametresi boş bir dizedir ve temel adres 0 (sıfır) olur.  
  
 `GetModuleInfo`Yöntemi modülün kimliği mevcut olduğu anda çağrılabilir olsa da, ana DERLEMENIN kimliği, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.  
  
 `GetModuleInfo`' İ döndüğünde, `szName` arabelleğin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için, işaret eden değeri `pcchName` parametresinin değeriyle karşılaştırın `cchName` . Daha `pcchName` büyük bir değere işaret ediyorsa `cchName` , daha büyük bir `szName` arabellek ayırır, `cchName` Yeni, daha büyük boyutla güncelleştirin ve `GetModuleInfo` yeniden çağırın.  
  
 Alternatif olarak, `GetModuleInfo` `szName` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcchName` ve `GetModuleInfo` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
- [GetModuleInfo2 Yöntemi](icorprofilerinfo3-getmoduleinfo2-method.md)
