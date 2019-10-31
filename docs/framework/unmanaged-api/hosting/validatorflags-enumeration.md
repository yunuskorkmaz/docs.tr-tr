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
ms.openlocfilehash: 61aafb8dc99bb908fc603945ff6ea74054f812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141425"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags Numaralandırması
[ICLRValidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metoduna yapılan bir çağrıda gerçekleştirilmesi gereken doğrulamanın türünü belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`VALIDATOR_CHECK_ILONLY`|Yürütülebilir dosyadaki yalnızca Microsoft ara dili 'nin (MSIL) doğrulanması gerektiğini belirtir.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Yalnızca yürütülebilir dosyanın biçiminin doğrulanması gerektiğini belirtir.|  
|`VALIDATOR_EXTRA_VERBOSE`|Tüm doğrulama türlerinin üzerinde gerçekleştirilmesi ve bildirilmesi gerektiğini belirtir.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Yürütülebilir dosyanın biçiminin doğrulanmamış olması gerektiğini belirtir.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Doğrulama hatası iletilerinin, doğrulama hatalarını oluşturan kaynak kodu satırlarını içermesi gerektiğini belirtir. Bu alan değeri 2,0 .NET Framework sürümünde geçerli değildir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator. IDL, IValidator. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
