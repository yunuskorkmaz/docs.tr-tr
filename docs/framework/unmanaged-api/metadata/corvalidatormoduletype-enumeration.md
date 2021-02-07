---
description: 'Daha fazla bilgi edinin: CorValidatorModuleType numaralandırması'
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
ms.openlocfilehash: 13792c461660ddd8cfd530f5b34d642d806cdea4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707273"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType Numaralandırması

Modülün türünü belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
|Üye|Description|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Modül geçersiz bir tür.|  
|`ValidatorModuleTypeMin`|Sabit listesinin en küçük değeri `CorValidatorModuleType` .|  
|`ValidatorModuleTypePE`|Modül, taşınabilir bir çalıştırılabilir (PE) dosyasıdır.|  
|`ValidatorModuleTypeObj`|Modül bir. obj dosyasıdır.|  
|`ValidatorModuleTypeEnc`|Modül, Düzenle ve devam et hata ayıklayıcı oturumundur.|  
|`ValidatorModuleTypeIncr`|Modül artımlı olarak oluşturulan bir modüldür.|  
|`ValidatorModuleTypeMax`|Sabit listesinin en büyük değeri `CorValidatorModuleType` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
