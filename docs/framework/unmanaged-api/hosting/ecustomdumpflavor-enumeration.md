---
title: ECustomDumpFlavor Numaralandırması
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124924"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor Numaralandırması
Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ECustomDumpFlavor` türünde bir parametre [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
