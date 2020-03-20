---
title: IMetaDataError::OnError Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177392"
---
# <a name="imetadataerroronerror-method"></a>IMetaDataError::OnError Yöntemi
Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hrError`  
 [içinde] HRESULT hata değeri arama yöntemine döndürülür.  
  
 `token`  
 [içinde] Hata oluştuğunda birleştirilen kod nesnesinin meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataError Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
