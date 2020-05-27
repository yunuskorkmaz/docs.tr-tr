---
title: IMetaDataEmit::SetClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008839"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout Yöntemi
Önceki bir [DefineTypeDef yöntemi](imetadataemit-definetypedef-method.md)çağrısıyla tanımlanmış bir sınıf için alanların yerleşimini tamamlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki `mdTypeDef`Çıkarılacak sınıfı belirten bir belirteç.  
  
 `dwPackSize`  
 'ndaki Paketleme boyutu: 1, 2, 4, 8 veya 16 bayt. Paketleme boyutu bitişik alanlar arasındaki baytların sayısıdır.  
  
 `rFieldOffsets`  
 'ndaki Her biri sınıfının bir alanını ve alanın içindeki sapmasını belirten [COR_FIELD_OFFSET](cor-field-offset-structure.md) yapılarının bir dizisi. Diziyi ile sonlandırın `mdTokenNil` .  
  
 `ulClassSize`  
 'ndaki Sınıfın bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı ilk olarak [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md) yöntemi çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık. Normal olarak, Otomatik düzeni kullanır ve çalışma zamanının alanları düzenlemenin en iyi yolunu seçmesini sağlayabilirsiniz.  
  
 Ancak, alanların yönetilmeyen kodun kullandığı düzenlemeye göre yerleşimini tercih edebilirsiniz. Bu durumda, `SetClassLayout` alanların yerleşimini tamamlamaya yönelik sıralı ya da açık Düzen ' i ve çağrı ' yı seçin:  
  
- Sıralı Düzen: paketleme boyutunu belirtin. Bir alan doğal boyutuna veya paketleme boyutuna göre hizalanır ve bu da alanın daha küçük bir uzaklığa neden olur. `rFieldOffsets`Ve öğesini `ulClassSize` sıfır olarak ayarlayın.  
  
- Açık Düzen: her alanın sapmasını belirtin ya da sınıf boyutunu ve paketleme boyutunu belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
