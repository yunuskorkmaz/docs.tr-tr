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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dcb9d5b3f1f47d6613be90f181a98ce991f697a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134854"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout Metodu
Belirtilen sınıf tarafından tanımlanan alanların bellekte Düzen hakkında bilgi alır. Diğer bir deyişle, bu yöntem, sınıfın alanlarının uzaklıkları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classID`  
 [in] Düzen alınacak sınıfın Kimliğidir.  
  
 `rFieldOffset`  
 [out içinde] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları belirteçleri ve ofsetleri sınıfın alanlarının her biri içerir.  
  
 `cFieldOffset`  
 [in] Boyutu `rFieldOffset` dizisi.  
  
 `pcFieldOffset`  
 [out] Kullanılabilir öğeleri toplam sayısı için bir işaretçi. Varsa `cFieldOffset` 0'dır, bu değer gerekli öğelerin sayısını gösterir.  
  
 `pulClassSize`  
 [out] Sınıf bayt cinsinden boyutunu içeren bir konum için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassLayout` Yöntemi yalnızca sınıfı tarafından tanımlanan alanları döndürür. Sınıfının üst sınıfı alanlar da tanımlanmışsa, profil oluşturucu çağırmanız gerekir `GetClassLayout` alanlarla elde etmek için üst sınıfta.  
  
 Kullanırsanız `GetClassLayout` dize sınıflarıyla yöntemi E_INVALIDARG hata koduyla başarısız olur. Kullanım [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) bir dizenin düzeni hakkında bilgi almak için. `GetClassLayout` Ayrıca bir dizi sınıfıyla çağrıldığında başarısız olur.  
  
 Sonra `GetClassLayout` döndürür, doğrulamalısınız `rFieldOffset` arabellek kullanılabilir tüm içerecek şekilde büyük `COR_FIELD_OFFSET` yapıları. Bunu yapmak için değeri ile karşılaştırmak, `pcFieldOffset` işaret boyutu ile `rFieldOffset` boyutu tarafından ayrılmış bir `COR_FIELD_OFFSET` yapısı. Varsa `rFieldOffset` büyük değil yeterince büyük bir ayırma `rFieldOffset` arabellek, güncelleştirme `cFieldOffset` yeni, daha büyük bir boyut ve çağrı `GetClassLayout` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetClassLayout` sıfır uzunluklu ile `rFieldOffset` arabellek doğru arabellek boyutu elde edilir. Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcFieldOffset` ve çağrı `GetClassLayout` yeniden.  
  
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
