---
title: ESymbolReadingPolicy Numaralandırması
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ba29952fe4a6edfc6e9e80ec02f82de65ef0064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208429"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy Numaralandırması
Program veritabanı (PDB) dosyaları okumak için ilkeyi değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Hata ayıklayıcı her zaman PDB dosyaları okuyup belirtir.|  
|`eSymbolReadingFullTrustOnly`|Hata ayıklayıcı tam güven derlemeleri ile ilişkili olan PDB dosyaları okuyup belirtir.|  
|`eSymbolReadingNever`|Hata ayıklayıcı, PDB dosyaları hiçbir zaman okuyup belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ESymbolReadingPolicy` Numaralandırması ile kullanılan [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
