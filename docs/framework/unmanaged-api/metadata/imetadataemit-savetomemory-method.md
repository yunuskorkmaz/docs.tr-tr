---
title: IMetaDataEmit::SaveToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177575"
---
# <a name="imetadataemitsavetomemory-method"></a>IMetaDataEmit::SaveToMemory Yöntemi
Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbData`  
 [çıkış] Meta veri yazmaya başlanacak adres.  
  
 `cbData`  
 [içinde] Ayrılan belleğin boyutu, baytlar içinde.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
