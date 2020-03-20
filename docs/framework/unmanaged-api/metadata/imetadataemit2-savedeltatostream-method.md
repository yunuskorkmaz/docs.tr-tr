---
title: IMetaDataEmit2::SaveDeltaToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177420"
---
# <a name="imetadataemit2savedeltatostream-method"></a>IMetaDataEmit2::SaveDeltaToStream Yöntemi
Değişiklikleri geçerli düzenle ve devam oturumundan belirtilen akışa kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pIStream`  
 [içinde] Değişiklikleri kaydetmek için yazılabilir akış için bir arabirim işaretçisi.  
  
 `dwSaveFlags`  
 [içinde] Saklı -dır. Bu değer sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
