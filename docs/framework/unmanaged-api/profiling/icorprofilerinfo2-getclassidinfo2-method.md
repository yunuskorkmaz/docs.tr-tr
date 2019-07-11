---
title: ICorProfilerInfo2::GetClassIDInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 892379d3281a98821b7feb5250973fac74f1f4f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751852"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 Yöntemi
Meta verileri ve üst modül için belirtilen sınıf, açık genel tanımını belirtecini alır `ClassID` kendi üst sınıfın ve `ClassID` her tür bağımsız değişkeni, sınıfın varsa.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 [in] Bilgileri alınır sınıfın Kimliğidir.  
  
 `pModuleId`  
 [out] Belirtilen sınıfın açık genel tanımının üst modül kimliği için işaretçi.  
  
 `pTypeDefToken`  
 [out] Meta veri belirteci açık genel belirtilen sınıf tanımına yönelik işaretçi.  
  
 `pParentClassId`  
 [out] Üst sınıf kimliği için işaretçi.  
  
 `cNumTypeArgs`  
 [in] Boyutu `typeArgs` dizisi.  
  
 `pcNumTypeArgs`  
 [out] Kullanılabilir öğeleri toplam sayısı için işaretçi.  
  
 `typeArgs`  
 [out] Bir dizi `ClassID` değerler, her biri bir tür bağımsız değişkeni sınıfın Kimliğini temsil eder. Yöntem döndürüldüğünde `typeArgs` bazı veya tüm kullanılabilir içerecek `ClassID` değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassIDInfo2` Yöntemi benzer [Icorprofilerınfo::getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemi, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgi alır.  
  
 Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) almak için bir [meta verileri](../../../../docs/framework/unmanaged-api/metadata/index.md) belirli bir modül için arabirim. Tarafından başvurulan konuma döndürülen meta veri belirteci `pTypeDefToken` sınıfı için meta veriler erişmek için kullanılabilir.  
  
 Sonra `GetClassIDInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri. Bunu yapmak için değeri ile karşılaştırmak, `pcNumTypeArgs` değeriyle işaret `cNumTypeArgs` parametresi. Varsa `pcNumTypeArgs` işaret değerinden daha büyük bir değere `cNumTypeArgs`, daha büyük bir ayırma `typeArgs` arabellek, güncelleştirme `cNumTypeArgs` yeni, daha büyük bir boyut ve çağrı `GetClassIDInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetClassIDInfo2` sıfır uzunluklu ile `typeArgs` arabellek doğru arabellek boyutu elde edilir. Ardından ayarlayabilirsiniz `typeArgs` arabellek boyutu döndürülen değere `pcNumTypeArgs` ve çağrı `GetClassIDInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
