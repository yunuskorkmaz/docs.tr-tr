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
ms.openlocfilehash: 9b03dc5460875af3bb3e5e20799a4d26eb74da05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730376"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler Yöntemi

Belirtilen işaretçinin başvurduğu yöntemi, `IUnknown` belirteç yeniden eşlemeleri için bir bildirim geri çağırması olarak ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pUnk`  
 'ndaki Kaydolmak için işleyici.  
  
## <a name="remarks"></a>Açıklamalar  

 Meta veri altyapısı, tarafından tarafından sunulan yöntemi kullanarak `SetHandler` , iyileştirilmiş bir şekilde kayıt üretmeyen ve kaydedilen kayıtları iyileştirmek istediğiniz derleyiciler için bildirim gönderir.  
  
 Geri çağırma yöntemi aracılığıyla sağlanmazsa `SetHandler` , farklı içeri aktarma kapsamlarının `IMapToken` her kapsam için birleştirme sırasında birleştirilmiş olması dışında, kaydetme sırasında hiçbir iyileştirme gerçekleştirilmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
