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
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout Metodu
Belirtilen sınıf tarafından tanımlanan alanların bellekte düzeni hakkındaki bilgileri alır. Diğer bir deyişle, bu yöntem sınıfın alanları uzaklıklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classID`  
 [in] Düzen alınır sınıfı kimliği.  
  
 `rFieldOffset`  
 [içinde out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları, belirteçleri ve uzaklıkları sınıfının alanlarının her biri içerir.  
  
 `cFieldOffset`  
 [in] Boyutunu `rFieldOffset` dizi.  
  
 `pcFieldOffset`  
 [out] Kullanılabilir öğeleri toplam sayısı için bir işaretçi. Varsa `cFieldOffset` 0'dır, bu değer gerekli öğe sayısını belirtir.  
  
 `pulClassSize`  
 [out] Sınıfının bayt cinsinden boyutu içeren bir konuma bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassLayout` Yöntemi yalnızca sınıf tarafından tanımlanan alanları döndürür. Profil Oluşturucu sınıfın üst sınıfı'de alanları tanımlamış ise çağırmalıdır `GetClassLayout` alanlarla elde etmek için üst sınıfı.  
  
 Kullanırsanız `GetClassLayout` dize sınıflarıyla yöntemi E_INVALIDARG hata koduyla başarısız olur. Kullanım [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) bir dize Düzen hakkında bilgi almak için. `GetClassLayout` Ayrıca bir dizi sınıf çağrıldığında başarısız olur.  
  
 Sonra `GetClassLayout` döndürür, doğrulamalısınız `rFieldOffset` arabellek tüm kullanılabilir içerecek şekilde büyük `COR_FIELD_OFFSET` yapıları. Bunu yapmak için değeri karşılaştırın, `pcFieldOffset` işaret boyutu ile `rFieldOffset` boyutu tarafından ayrılmış bir `COR_FIELD_OFFSET` yapısı. Varsa `rFieldOffset` büyük değil yeterince büyük bir ayırma `rFieldOffset` arabellek, güncelleştirme `cFieldOffset` yeni, büyük boyutu ve çağrı `GetClassLayout` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetClassLayout` sıfır uzunluklu ile `rFieldOffset` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcFieldOffset` ve arama `GetClassLayout` yeniden.  
  
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
