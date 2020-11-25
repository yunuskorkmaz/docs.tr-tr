---
title: IMetaDataValidate::ValidatorInit Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: e2f54e11906cd4ba1440e220530f2ca5b9de769f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708562"
---
# <a name="imetadatavalidatevalidatorinit-method"></a>IMetaDataValidate::ValidatorInit Yöntemi

Geçerli meta veri kapsamındaki modülün türünü belirten bir bayrak ayarlar ve doğrulama hataları için belirtilen geri çağırma yöntemini kaydeder.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwModule`  
 'ndaki Geçerli meta veri kapsamındaki modülün türünü belirten [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) numaralandırması değeri.  
  
 `pUnk`  
 'ndaki Doğrulama hataları için işlev geri çağırması görevi gören bir [IUnknown](/cpp/atl/iunknown) örneği işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataValidate Arabirimi](imetadatavalidate-interface.md)
