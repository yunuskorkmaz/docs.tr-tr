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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e22cf8e540bfdb53ad243640dac110b5750e53e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout Yöntemi
Önceki bir çağrı tarafından tanımlanan bir sınıf için alanlarının düzenini tamamlandıktan [DefineTypeDef yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Bir `mdTypeDef` düzenlendiği için sınıf belirtir belirteci.  
  
 `dwPackSize`  
 [in] Paket boyutu: 1, 2, 4, 8 veya 16 bayt. Paket boyutu bitişik alanlar arasında bayt sayısıdır.  
  
 `rFieldOffsets`  
 [in] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları, her biri belirtir sınıfının bir alanı ve alan sınıf içinde uzaklığı. Dizi ile sonlandırmak `mdTokenNil`.  
  
 `ulClassSize`  
 [in] Sınıfının bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı, başlangıçta çağırarak tanımlanır [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi ve sınıfın alanları için üç düzenleri birini belirterek: otomatik, sıralı ya da açık. Normalde, otomatik düzenini kullanın ve alanları düzenlemek için en iyi yolu seçin çalışma zamanı izin.  
  
 Bununla birlikte, kod kullandığı yönetilmeyen düzenlemeyi göre yerleştirilmiş normal bir kutudur alanları isteyebilirsiniz. Bu durumda, sıralı veya açık düzenini çağrısı seçip `SetClassLayout` alanlarının düzenini tamamlamak için:  
  
-   Ardışık Düzen: paket boyutu belirtin. Bir alan doğal boyutu veya paket boyutu, alan daha küçük uzaklığını hangi sonuçlarında göre hizalanır. Ayarlama `rFieldOffsets` ve `ulClassSize` sıfır.  
  
-   Açık düzene: her bir alan uzaklığını ya da sınıf boyutu ve paket boyutu belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
