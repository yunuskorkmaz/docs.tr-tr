---
title: "ValidatorFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 952944e9ae9a8186a182796deb587b6fa6a0d6a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags Numaralandırması
Çağrıda gerçekleştirilmelidir doğrulama türünü belirtmek değerleri içeren [Iclrvalidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Yalnızca Microsoft Ara dilde (MSIL) yürütülebilir dosyası doğrulanması gerektiğini belirtir.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Yalnızca yürütülebilir dosyasının biçimi doğrulanmalıdır belirtir.|  
|`VALIDATOR_EXTRA_VERBOSE`|Her türlü doğrulama gerçekleştirilen ve bildirilen belirtir.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Yürütülebilir dosya biçimi doğrulanmazsa belirtir.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Doğrulama hatası iletilerinin doğrulama hataları Yükselt kaynak kod satırlarını içermelidir belirtir. Bu alanın değeri .NET Framework 2.0 sürümünde geçerli değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** IValidator.idl, IValidator.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
