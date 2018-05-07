---
title: ICorProfilerInfo2::GetClassIDInfo2 Metodu
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
ms.openlocfilehash: 2af0eacbff8220be7f2286f7f345f14126972261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 Metodu
Meta verileri ve üst modül için belirtilen sınıfın açık genel tanımını belirtecini alır `ClassID` kendi üst sınıfın ve `ClassID` sınıfının varsa, her türü değişkeni.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] Bilgiler alınır sınıfı kimliği.  
  
 `pModuleId`  
 [out] Belirtilen sınıf açık genel tanımı için üst modülü Kimliğini işaretçi.  
  
 `pTypeDefToken`  
 [out] Belirtilen sınıf açık genel tanımı için meta veri simgesi işaretçi.  
  
 `pParentClassId`  
 [out] Üst sınıf kimliği için işaretçi.  
  
 `cNumTypeArgs`  
 [in] Boyutunu `typeArgs` dizi.  
  
 `pcNumTypeArgs`  
 [out] İşaretçi kullanılabilir öğelerin toplam sayısı.  
  
 `typeArgs`  
 [out] Bir dizi `ClassID` değerleri, her biri bir tür bağımsız değişkeni sınıfının Kimliğini temsil eder. Yöntem döndüğünde `typeArgs` bazı veya tüm kullanılabilir içerecek `ClassID` değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassIDInfo2` Yöntemi benzer [Icorprofilerınfo::getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemi, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgi alır.  
  
 Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) elde etmek için bir [meta veri](../../../../docs/framework/unmanaged-api/metadata/index.md) verilen modülü için arabirim. Tarafından başvurulan konuma döndürülen meta veri simgesi `pTypeDefToken` sınıfı için meta verilerine erişmek için kullanılabilir.  
  
 Sonra `GetClassIDInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri. Bunu yapmak için değeri karşılaştırın, `pcNumTypeArgs` değeriyle işaret `cNumTypeArgs` parametresi. Varsa `pcNumTypeArgs` işaret eden daha büyük bir değere `cNumTypeArgs`, daha geniş bir ayırma `typeArgs` arabellek, güncelleştirme `cNumTypeArgs` yeni, büyük boyutu ve çağrı `GetClassIDInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetClassIDInfo2` sıfır uzunluklu ile `typeArgs` arabellek doğru arabellek boyutu elde edilir. Ardından ayarlayabilirsiniz `typeArgs` arabellek boyutu için döndürülen değer `pcNumTypeArgs` ve arama `GetClassIDInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
