---
title: IMetaDataEmit::SetHandler Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177538"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler Yöntemi
Belirtilmiş `IUnknown` işaretçi tarafından başvurulan yöntemi belirteç yeniden eşlemleri için bildirim geri araması olarak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pUnk`  
 [içinde] Kayıt için işleyici.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri altyapısı, kayıtları en iyi duruma `SetHandler`getirilmiş bir şekilde oluşturmayan ve kaydedilen kayıtları en iyi duruma getirmek için derleyicilere , tarafından sağlanan yöntemi kullanarak bildirim gönderir.  
  
 Geri arama yöntemi aracılığıyla `SetHandler`sağlanmazsa, her kapsam için birleştirme kullanılarak `IMapToken` birkaç alma kapsamının birleştirilmesi dışında kayda geçirilme işlemi yapılmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
