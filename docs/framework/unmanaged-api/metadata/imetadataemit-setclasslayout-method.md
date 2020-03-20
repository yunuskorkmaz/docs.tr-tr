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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177570"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout Yöntemi
[DefineTypeDef Yöntemi'ne](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)önceki bir çağrıyla tanımlanan bir sınıfın alanlarının düzenini tamamlar.  
  
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
 [içinde] Ortaya `mdTypeDef` konacak sınıfı belirten bir belirteç.  
  
 `dwPackSize`  
 [içinde] Ambalaj boyutu: 1, 2, 4, 8 veya 16 bayt. Paketleme boyutu, bitişik alanlar arasındaki bayt sayısıdır.  
  
 `rFieldOffsets`  
 [içinde] Her biri sınıfın bir alanını ve sınıfın içindeki alanın ofsetini belirten [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları dizisi. Diziyi `mdTokenNil`' ile sonlandırın.  
  
 `ulClassSize`  
 [içinde] Sınıfın büyüklüğü, baytlar halinde.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf başlangıçta [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık. Normalde, otomatik düzeni kullanır ve çalışma zamanı alanları düzenlemek için en iyi yolu seçmesine izin.  
  
 Ancak, yönetilmeyen kodun kullandığı düzenlemeye göre alanların düzenlenmesini isteyebilirsiniz. Bu durumda, alanların düzenini tamamlamak `SetClassLayout` için sıralı veya açık düzeni seçin ve arayın:  
  
- Sıralı düzen: Ambalaj boyutunu belirtin. Bir alan, alanın daha küçük ofset ile sonuçlandığı doğal boyutuna veya ambalaj boyutuna göre hizalanır. Ayarlayın `rFieldOffsets` `ulClassSize` ve sıfıra ayarlayın.  
  
- Açık düzen: Her alanın mahsupını belirtin veya sınıf boyutunu ve ambalaj boyutunu belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
