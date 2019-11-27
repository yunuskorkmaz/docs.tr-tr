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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441770"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout Yöntemi
Önceki bir [DefineTypeDef yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)çağrısıyla tanımlanmış bir sınıf için alanların yerleşimini tamamlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki Çıkarılacak sınıfı belirten `mdTypeDef` belirteci.  
  
 `dwPackSize`  
 'ndaki Paketleme boyutu: 1, 2, 4, 8 veya 16 bayt. Paketleme boyutu bitişik alanlar arasındaki baytların sayısıdır.  
  
 `rFieldOffsets`  
 'ndaki Her biri sınıfının bir alanını ve alanın içindeki sapmasını belirten [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapılarının bir dizisi. Diziyi `mdTokenNil`sonlandırın.  
  
 `ulClassSize`  
 'ndaki Sınıfın bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı ilk olarak [ımetadatayayma::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık. Normal olarak, Otomatik düzeni kullanır ve çalışma zamanının alanları düzenlemenin en iyi yolunu seçmesini sağlayabilirsiniz.  
  
 Ancak, alanların yönetilmeyen kodun kullandığı düzenlemeye göre yerleşimini tercih edebilirsiniz. Bu durumda, alanların yerleşimini tamamlamaya yönelik sıralı veya açık Düzen ' i seçin ve `SetClassLayout` çağırın:  
  
- Sıralı Düzen: paketleme boyutunu belirtin. Bir alan doğal boyutuna veya paketleme boyutuna göre hizalanır ve bu da alanın daha küçük bir uzaklığa neden olur. `rFieldOffsets` ve `ulClassSize` sıfır olarak ayarlayın.  
  
- Açık Düzen: her alanın sapmasını belirtin ya da sınıf boyutunu ve paketleme boyutunu belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
