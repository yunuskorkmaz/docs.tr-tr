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
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429741"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy Numaralandırması
Program veritabanı (PDB) dosyaları okumak için ilke ayarlama değerlerini içerir.  
  
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
|`eSymbolReadingAlways`|Hata ayıklayıcı PDB dosyaları her zaman okumalısınız belirtir.|  
|`eSymbolReadingFullTrustOnly`|Hata ayıklayıcı tam güven derlemeler ile ilişkilendirilmiş PDB dosyalarını okumalısınız belirtir.|  
|`eSymbolReadingNever`|Hata ayıklayıcı PDB dosyalarını hiçbir zaman okumalısınız belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ESymbolReadingPolicy` Numaralandırması ile kullanılır [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
