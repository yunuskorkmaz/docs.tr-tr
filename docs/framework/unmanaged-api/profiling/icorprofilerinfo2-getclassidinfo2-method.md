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
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433428"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 Yöntemi
Belirtilen sınıfın açık genel tanımına, üst sınıfının `ClassID` ve varsa sınıfının her bir tür bağımsız değişkeni için `ClassID` ait üst modülü ve meta veri belirtecini alır.  
  
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
 'ndaki Bilgilerin alınacağı sınıfın KIMLIĞI.  
  
 `pModuleId`  
 dışı Belirtilen sınıfın açık genel tanımının üst modülünün KIMLIĞINE yönelik işaretçi.  
  
 `pTypeDefToken`  
 dışı Belirtilen sınıfın açık genel tanımı için meta veri belirtecinin işaretçisi.  
  
 `pParentClassId`  
 dışı Üst sınıfın KIMLIĞINE yönelik işaretçi.  
  
 `cNumTypeArgs`  
 'ndaki `typeArgs` dizisinin boyutu.  
  
 `pcNumTypeArgs`  
 dışı Kullanılabilir öğelerin toplam sayısına yönelik işaretçi.  
  
 `typeArgs`  
 dışı Her biri sınıfının bir tür bağımsız değişkeninin KIMLIĞINI temsil eden `ClassID` değerleri dizisi. Yöntemi döndürüldüğünde `typeArgs`, kullanılabilir `ClassID` değerlerinin bazılarını veya tümünü içerecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassIDInfo2` yöntemi [ICorProfilerInfo:: GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemine benzer, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgiler elde eder.  
  
 Profil Oluşturucu kodu, belirli bir modül için [meta](../../../../docs/framework/unmanaged-api/metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. `pTypeDefToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra sınıfının meta verilerine erişmek için kullanılabilir.  
  
 `GetClassIDInfo2` çağrıldıktan sonra, `typeArgs` arabelleğinin tüm `ClassID` değerlerini içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcNumTypeArgs` işaret eden değeri `cNumTypeArgs` parametresinin değeri ile karşılaştırın. `pcNumTypeArgs`, `cNumTypeArgs`daha büyük bir değere işaret ediyorsa, daha büyük bir `typeArgs` arabelleği ayırın, yeni, daha büyük boyuttaki `cNumTypeArgs` güncelleştirin ve `GetClassIDInfo2` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetClassIDInfo2` sıfır uzunluklu `typeArgs` arabelleği ile çağırabilirsiniz. Daha sonra `typeArgs` arabellek boyutunu `pcNumTypeArgs` döndürülen değere ayarlayabilir ve `GetClassIDInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
