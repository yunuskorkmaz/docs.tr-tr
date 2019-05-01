---
title: ValidatorFlags Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa10ae1cf67339a6719210f3162f19ac648e8ee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942356"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags Numaralandırması
Bir çağrıda gerçekleştirilmelidir doğrulama türünü gösteren değerleri içerir [Iclrvalidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) yöntemi.  
  
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
|`VALIDATOR_CHECK_ILONLY`|Yalnızca Microsoft Ara dilini (MSIL) yürütülebilir dosyasına doğrulanmalıdır belirtir.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Sadece yürütülebilir dosya biçimi doğrulanmalıdır belirtir.|  
|`VALIDATOR_EXTRA_VERBOSE`|Tüm doğrulama türlerinin gerçekleştirilen ve üzerinde bildirilen belirtir.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Yürütülebilir dosya biçiminin geçerliliğinin doğrulanması belirtir.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Doğrulama hatası iletilerinin doğrulama hatalarını yükseltmek kaynak kodu satırlarını içermesi gerektiğini belirtir. Bu alanın değeri, .NET Framework 2.0 sürümünde geçerli değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator.idl, IValidator.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
