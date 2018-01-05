---
title: IMetaDataEmit::MergeEnd Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd Metodu
Birleştirmeler geçerli kapsam için bir veya daha fazla önceki çağrıları tarafından belirtilen tüm meta veri kapsamları [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yordam gerçek birleştirme meta verilerin tetikler, tüm kapsamlar çağrıları koyarak belirtilen alma `IMetaDataEmit::Merge`, geçerli çıkış kapsam içine.  
  
 Aşağıdaki özel koşullar birleştirme için geçerlidir:  
  
-   Meta veri alma kapsamında benzersiz olduğundan modülü sürüm tanıtıcısını (MVID) hiçbir zaman alınır.  
  
-   Varolan modülü genelinde özellik üzerine yazılır.  
  
     Modülü özellikleri zaten geçerli kapsam için ayarlandıysa, hiçbir modülü özellikleri içeri aktarılır. Modülü özellikleri geçerli kapsamda ayarlanmamış, yalnızca zaman ilk karşılaşılan sonra ancak bunlar içeri aktarılır. Bu modülü özellikleri yeniden aldıysanız, yinelenen oldukları. (MVID dışında) tüm modülü özelliklerinin değerlerini karşılaştırılır ve yinelenen bulunan, bir hata oluştu.  
  
-   Tür tanımları için (`TypeDef`), yinelenen geçerli kapsam birleştirilir. `TypeDef`nesneleri her karşı çoğaltmaları denetlenir *tam nesne adı* + *GUID* + *sürüm numarası*. Adı veya GUID bir eşleşme yoktur ve herhangi bir diğer iki farklı ise, bir hata oluştu. Aksi durumda, tüm üç öğe eşleşiyorsa `MergeEnd` girişleri gerçekten Tekrarların; sağlamak için basit bir denetim gerçekleştirir değilse, bir hata oluşur. Bu basit onay arar:  
  
    -   Aynı sırada gerçekleşen aynı üye bildirimleri. Olarak işaretlenmiş üyeleri `mdPrivateScope` (bkz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırması) bu iade; bulunmayan özel birleştirilir.  
  
    -   Aynı sınıf düzeni.  
  
     Bunun anlamı bir `TypeDef` nesne her zaman tam olarak ve tutarlı bir şekilde tanımlanması gerekir her meta veri kapsamda durumda bildirilmiş; bunun üye uygulamalarını (için bir sınıf) birden çok derleme biriminden yayılır, tam tanımı olarak kabul edilir Her kapsamda varsa ve her bir kapsama artımlı. Parametre adları sözleşmesine ilgili varsa, örneğin, bunlar aynı şekilde her kapsam içine yayınlaması gerekir; ilgili değilseniz, bunların meta verileri yayınlaması gerektiğini değil.  
  
     Özel durum olan bir `TypeDef` nesne artımlı üyeleri olarak işaretlenmiş olabilir `mdPrivateScope`. Bunlar, karşılaşmadan üzerine `MergeEnd` artımlı olarak bakmadan çoğaltmalar için geçerli bir kapsama ekler. Derleyici özel kapsam anlar olduğundan derleyici kural zorlama için sorumlu olmalıdır.  
  
-   Göreli sanal adresleri (RVAs) içeri aktarılan veya birleştirilmiş; Derleyici, bu bilgileri yeniden yayma olması beklenir.  
  
-   Özel öznitelikler yalnızca bağlı olan öğe birleştirildiğinde birleştirilir. Örneğin, bir sınıfla ilişkilendirilen özel öznitelikler sınıfı ilk karşılaşıldığında birleştirilir. Özel öznitelikler ilişkilendirilen bir `TypeDef` veya `MemberDef` , derleme birimine (örneğin, bir üye derleme zaman damgası) belirli, bunlar birleştirilmez ve kaldırmak veya bu tür meta verilerini güncelleştirmek için derleyici kadar olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
