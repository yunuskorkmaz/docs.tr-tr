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
ms.openlocfilehash: 64d2cd76dafb1a51814b916b5ce73fb08cdcaef9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868866"
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
 `GetClassIDInfo2` yöntemi [ICorProfilerInfo:: GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) yöntemine benzer, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgiler elde eder.  
  
 Profil Oluşturucu kodu, belirli bir modül için [meta](../../../../docs/framework/unmanaged-api/metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. `pTypeDefToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra sınıfının meta verilerine erişmek için kullanılabilir.  
  
 `GetClassIDInfo2` çağrıldıktan sonra, `typeArgs` arabelleğinin tüm `ClassID` değerlerini içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcNumTypeArgs` işaret eden değeri `cNumTypeArgs` parametresinin değeri ile karşılaştırın. `pcNumTypeArgs`, `cNumTypeArgs`daha büyük bir değere işaret ediyorsa, daha büyük bir `typeArgs` arabelleği ayırın, yeni, daha büyük boyuttaki `cNumTypeArgs` güncelleştirin ve `GetClassIDInfo2` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetClassIDInfo2` sıfır uzunluklu `typeArgs` arabelleği ile çağırabilirsiniz. Daha sonra `typeArgs` arabellek boyutunu `pcNumTypeArgs` döndürülen değere ayarlayabilir ve `GetClassIDInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
