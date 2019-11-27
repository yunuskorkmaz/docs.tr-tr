---
title: ICorProfilerInfo2::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433398"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout Metodu
Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır. Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classID`  
 'ndaki Düzenin alınacağı sınıfın KIMLIĞI.  
  
 `rFieldOffset`  
 [in, out] Her biri sınıfın alanlarının belirteçlerini ve farklarını içeren [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapılarından oluşan bir dizi.  
  
 `cFieldOffset`  
 'ndaki `rFieldOffset` dizisinin boyutu.  
  
 `pcFieldOffset`  
 dışı Kullanılabilir öğelerin toplam sayısına yönelik bir işaretçi. `cFieldOffset` 0 ise, bu değer gerekli öğelerin sayısını belirtir.  
  
 `pulClassSize`  
 dışı Sınıfının bayt cinsinden boyutunu içeren konuma yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassLayout` yöntemi yalnızca sınıfın kendisi tarafından tanımlanan alanları döndürür. Sınıfın üst sınıfı da tanımlı alanlar içeriyorsa, bu alanları almak için profil oluşturucunun üst sınıfta `GetClassLayout` çağrısı gerekir.  
  
 Dize sınıfları ile `GetClassLayout` kullanıyorsanız, yöntem E_INVALIDARG hata kodu ile başarısız olur. Bir dizenin düzeni hakkında bilgi almak için [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) kullanın. `GetClassLayout`, bir dizi sınıfıyla çağrıldığında de başarısız olur.  
  
 `GetClassLayout` çağrıldıktan sonra, `rFieldOffset` arabelleğinin tüm kullanılabilir `COR_FIELD_OFFSET` yapılarını içermesi için yeterince büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcFieldOffset` işaret eden değeri, `rFieldOffset` boyutuyla `COR_FIELD_OFFSET` yapısına bölünmüş şekilde karşılaştırın. `rFieldOffset` yeterince büyük değilse, daha büyük bir `rFieldOffset` arabelleği ayırın, yeni, daha büyük boyuttaki `cFieldOffset` güncelleştirin ve `GetClassLayout` yeniden çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetClassLayout` sıfır uzunluklu `rFieldOffset` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `pcFieldOffset` döndürülen değere ayarlayabilir ve `GetClassLayout` tekrar çağırabilirsiniz.  
  
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
