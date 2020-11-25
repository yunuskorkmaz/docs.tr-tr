---
title: IMetaDataEmit2::SaveDeltaToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: a4dbe090987248ef77ce371b5bc6fb42d898f726
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705416"
---
# <a name="imetadataemit2savedeltatomemory-method"></a>IMetaDataEmit2::SaveDeltaToMemory Yöntemi

Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbData`  
 dışı Meta veri değişim yazmanın başlayacağı adres.  
  
 `cbData`  
 'ndaki Değişikliklerin boyutu. Boyutunu öğrenmek için [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
