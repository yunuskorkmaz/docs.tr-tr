---
description: 'Daha fazla bilgi edinin: ValidatorFlags numaralandırması'
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
ms.openlocfilehash: 473b0eef2851126256e1ea6b6d2b82be32e03e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679127"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags Numaralandırması

[ICLRValidator:: Validate](iclrvalidator-validate-method.md) metoduna yapılan bir çağrıda gerçekleştirilmesi gereken doğrulamanın türünü belirten değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Yürütülebilir dosyadaki yalnızca Microsoft ara dili 'nin (MSIL) doğrulanması gerektiğini belirtir.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Yalnızca yürütülebilir dosyanın biçiminin doğrulanması gerektiğini belirtir.|  
|`VALIDATOR_EXTRA_VERBOSE`|Tüm doğrulama türlerinin üzerinde gerçekleştirilmesi ve bildirilmesi gerektiğini belirtir.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Yürütülebilir dosyanın biçiminin doğrulanmamış olması gerektiğini belirtir.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Doğrulama hatası iletilerinin, doğrulama hatalarını oluşturan kaynak kodu satırlarını içermesi gerektiğini belirtir. Bu alan değeri 2,0 .NET Framework sürümünde geçerli değildir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator. IDL, IValidator. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRErrorReportingManager Arabirimi](iclrerrorreportingmanager-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
