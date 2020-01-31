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
ms.openlocfilehash: 25c5568e4cae0ead82b59b09dbbb9a11e4bc2df2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863445"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo Yöntemi
Bir modül KIMLIĞI verildiğinde, modülün dosya adını ve modülün üst derleme KIMLIĞINI döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `szName` dönüş arabelleğinin karakter cinsinden uzunluğu.  
  
 `pcchName`  
 dışı Modülün dosya adının döndürülen toplam karakter uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Arayan tarafından sunulan geniş bir karakter arabelleği. Yöntem döndüğünde, bu arabellek modülün dosya adını içerir.  
  
 `pAssemblyId`  
 dışı Modülün üst derleme KIMLIĞINE yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modüller için `szName` parametresi boş bir dizedir ve temel adres 0 (sıfır) olur.  
  
 `GetModuleInfo` yöntemi modülün KIMLIĞI mevcut olduğu anda çağrılabilir olsa da, ana derlemenin KIMLIĞI, profil oluşturucu [ICorProfilerCallback:: ModuleAttachedToAssembly geri çağrısını](icorprofilercallback-moduleattachedtoassembly-method.md) alıncaya kadar kullanılamaz.  
  
 `GetModuleInfo` döndüğünde, `szName` arabelleğinin modülün tam dosya adını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcchName` işaret eden değeri `cchName` parametresinin değeri ile karşılaştırın. `pcchName`, `cchName`daha büyük bir değere işaret ediyorsa, daha büyük bir `szName` arabelleği ayırın, yeni, daha büyük boyuttaki `cchName` güncelleştirin ve `GetModuleInfo` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetModuleInfo` sıfır uzunluklu `szName` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcchName` döndürülen değere ayarlayabilir ve `GetModuleInfo` tekrar çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
- [GetModuleInfo2 Yöntemi](icorprofilerinfo3-getmoduleinfo2-method.md)
