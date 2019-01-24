---
title: IMetaDataEmit::MergeEnd Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45d85be4e4987e5a5234ca2d57c85a56f9f544bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657031"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd Metodu
Birleştirmeleri geçerli kapsam için bir veya daha fazla önceki çağrılar tarafından belirtilen tüm meta veri kapsamları [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yordam meta verilerinin gerçek birleştirme tetiklenir, tüm çağrıları koyarak Belirtilen kapsam içeri `IMetaDataEmit::Merge`, geçerli çıkış kapsama.  
  
 Birleştirme için aşağıdaki özel koşullar geçerlidir:  
  
-   Meta veri içeri aktarma kapsamı içinde benzersiz olduğu için modülü sürüm tanımlayıcısı (MVID) hiçbir zaman aktarılır.  
  
-   Mevcut hiçbir modül genelinde özellik üzerine yazılır.  
  
     Hiçbir modül özellik modülü özellikleri geçerli kapsam için zaten belirlenmişse içeri aktarılır. Modülü özellikleri geçerli kapsamda ayarlanmamış ise yalnızca zaman ilk karşılaşılan sonra ancak bunlar içeri aktarılır. Bu modülü özellikleri yeniden karşılaşılırsa, çoğaltmaları değildirler. Tüm modül özelliklerini (dışında MVID) değerlerini karşılaştırılır ve yinelenen öğeler bulundu, bir hata ortaya çıkar.  
  
-   Tür tanımları (`TypeDef`), yinelemelere geçerli kapsam birleştirilir. `TypeDef` nesneleri her karşı çoğaltmaları denetlenir *nesne tam adı* + *GUID* + *sürüm numarası*. Bir eşleşme adı veya GUID ve diğer iki öğelerden farklı ise, bir hata ortaya çıkar. Aksi durumda, tüm üç öğe eşleşiyorsa `MergeEnd` girişleri çoğaltmaları; aslında olduğundan emin olmak için basit bir denetim gerçekleştirir Aksi takdirde bir hata ortaya çıkar. Bu basit bir onay arar:  
  
    -   Aynı sırada gerçekleşen aynı üye bildirim kullanımları. Olarak işaretlenmiş üyeleri `mdPrivateScope` (bkz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırması) bu iade; bulunmayan özel birleştirilir.  
  
    -   Aynı sınıf düzeni.  
  
     Diğer bir deyişle bir `TypeDef` nesne her zaman tam olarak ve tutarlı bir şekilde tanımlanmalıdır her meta veri kapsamında, BT bildirilir; bunun üye uygulamalarını (için bir sınıf) arasında birden çok derleme biriminden yayılır, tam tanımı olarak kabul edilir Her kapsamda varsa ve her kapsam için artımlı. Parametre adları sözleşmesine uygun olan, örneğin, bunlar aynı şekilde her kapsamına yayılan gerekir; ilgili olmayan, bunların meta verilere yayılan değil.  
  
     Özel durum olan bir `TypeDef` nesne artımlı üyeleri olarak işaretlenmiş olabilir `mdPrivateScope`. Bunlar, karşılaşıldığında üzerinde `MergeEnd` artımlı olarak çoğaltmaları olmadan geçerli bir kapsama ekler. Derleyici özel kapsam anlayan olduğundan derleyici kurallar uygulamaktan sorumlu olması gerekir.  
  
-   Göreli sanal adreslerine (RVA) içeri aktarılan veya birleştirilmiş; Derleyici bu bilgileri yeniden yayma bekleniyor.  
  
-   Özel öznitelikler, bağlı öğe birleştirildiğinde birleştirilir. Örneğin, sınıf ilk karşılaşıldığında bir sınıf ile ilişkili özel öznitelikler birleştirilir. Özel öznitelikler ilişkilendirilen bir `TypeDef` veya `MemberDef` derleme birimi (örneğin, bir üye derleme zaman damgasını) özgü olan, birleştirilmiş değil ve kaldırın veya bu tür meta verileri güncelleştirmek için derleyici en fazla olan.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
