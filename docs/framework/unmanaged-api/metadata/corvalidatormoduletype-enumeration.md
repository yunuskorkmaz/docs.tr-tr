---
title: CorValidatorModuleType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee1cfe52caa9d727a132d7adc23b03575293db65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716784"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType Numaralandırması
Bir modül türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Modül geçersiz bir türdür.|  
|`ValidatorModuleTypeMin`|En küçük değerini `CorValidatorModuleType` sabit listesi.|  
|`ValidatorModuleTypePE`|Modül bir taşınabilir yürütülebilir (PE) dosyasıdır.|  
|`ValidatorModuleTypeObj`|Bir .obj dosyası modülüdür.|  
|`ValidatorModuleTypeEnc`|Düzenle ve devam et hata ayıklayıcı oturumu modülüdür.|  
|`ValidatorModuleTypeIncr`|Artımlı olarak derlenen bir modüldür.|  
|`ValidatorModuleTypeMax`|En büyük değerini `CorValidatorModuleType` sabit listesi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
