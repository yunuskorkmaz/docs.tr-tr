---
title: IMetaDataEmit::Merge Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175713"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge Yöntemi
Belirtilen alınan kapsamı birleştirilecek kapsamlar listesine ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pImport`  
 [içinde] Birleştirilecek dışa aktarılan kapsamı tanımlayan bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) nesnesinin işaretçisi.  
  
 `pIMap`  
 [içinde] Belirteç yeniden eşlemi belirten bir [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) nesnesine işaretçi.  
  
 `pHandler`  
 [içinde] Hataları belirten [bir IUnknown](/cpp/atl/iunknown) nesnesine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) tek bir kapsamda meta verilerin birleşmesi tetiklemek için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
