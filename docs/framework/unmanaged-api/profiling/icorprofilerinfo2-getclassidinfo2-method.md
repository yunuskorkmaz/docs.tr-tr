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
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497172"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 Yöntemi
Belirtilen sınıfın açık genel tanımının, `ClassID` üst sınıfının ve varsa `ClassID` sınıfının her tür bağımsız değişkeni için üst modülü ve meta veri belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `typeArgs`Dizinin boyutu.  
  
 `pcNumTypeArgs`  
 dışı Kullanılabilir öğelerin toplam sayısına yönelik işaretçi.  
  
 `typeArgs`  
 dışı `ClassID`Her biri sınıfının bir tür bağımsız DEĞIŞKENININ kimliğini temsil eden bir değer dizisi. Yöntemi döndüğünde, `typeArgs` kullanılabilir değerlerin bazılarını veya tümünü içerecektir `ClassID` .  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassIDInfo2`Yöntemi [ICorProfilerInfo:: GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) yöntemine benzer, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgiler edinir.  
  
 Profil Oluşturucu kodu, belirli bir modül için [meta](../metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. Tarafından başvurulan konuma döndürülen meta veri belirteci, `pTypeDefToken` daha sonra sınıfının meta verilerine erişmek için kullanılabilir.  
  
 `GetClassIDInfo2`Geri döndüğünde, `typeArgs` arabelleğin tüm değerleri içerecek kadar büyük olduğunu doğrulamanız gerekir `ClassID` . Bunu yapmak için, işaret eden değeri `pcNumTypeArgs` parametresinin değeriyle karşılaştırın `cNumTypeArgs` . Daha `pcNumTypeArgs` büyük bir değere işaret ediyorsa `cNumTypeArgs` , daha büyük bir `typeArgs` arabellek ayırır, `cNumTypeArgs` Yeni, daha büyük boyutla güncelleştirin ve `GetClassIDInfo2` yeniden çağırın.  
  
 Alternatif olarak, `GetClassIDInfo2` `typeArgs` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `typeArgs` arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcNumTypeArgs` ve `GetClassIDInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
