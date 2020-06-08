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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497159"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout Metodu
Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır. Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in, out] Her biri sınıfın alanlarının belirteçlerini ve farklarını içeren [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) yapılarından oluşan bir dizi.  
  
 `cFieldOffset`  
 'ndaki `rFieldOffset`Dizinin boyutu.  
  
 `pcFieldOffset`  
 dışı Kullanılabilir öğelerin toplam sayısına yönelik bir işaretçi. `cFieldOffset`0 ise, bu değer gereken öğe sayısını gösterir.  
  
 `pulClassSize`  
 dışı Sınıfının bayt cinsinden boyutunu içeren konuma yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassLayout`Yöntemi yalnızca sınıfın kendisi tarafından tanımlanan alanları döndürür. Sınıfın üst sınıfı tanımlanmış alanları da varsa, `GetClassLayout` Bu alanları almak için profil oluşturucunun üst sınıfta çağrısı gerekir.  
  
 `GetClassLayout`Dize sınıfları ile kullanıyorsanız, yöntem E_INVALIDARG hata kodu ile başarısız olur. Bir dizenin düzeni hakkında bilgi almak için [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) kullanın. `GetClassLayout`, bir dizi sınıfıyla çağrıldığında de başarısız olur.  
  
 `GetClassLayout`Geri döndüğünde, `rFieldOffset` arabelleğin tüm kullanılabilir yapıları içermesi için yeterince büyük olduğunu doğrulamanız gerekir `COR_FIELD_OFFSET` . Bunu yapmak için, ile işaret edilen değeri, `pcFieldOffset` `rFieldOffset` bir yapının boyutuna bölünen boyutla karşılaştırın `COR_FIELD_OFFSET` . `rFieldOffset`Yeterince büyük değilse, daha büyük bir arabellek ayırın `rFieldOffset` , `cFieldOffset` Yeni, daha büyük boyutla güncelleştirin ve `GetClassLayout` yeniden çağırın.  
  
 Alternatif olarak, `GetClassLayout` `rFieldOffset` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcFieldOffset` ve `GetClassLayout` yeniden çağırabilirsiniz.  
  
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
