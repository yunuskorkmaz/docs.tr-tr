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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d0ba3f722f63650a3db6a8f633189993db0716
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431414"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor Numaralandırması
Hata raporlama yapılırken bir öbek içinde bir özel alt dahil edilecek maddeleri dökümü belirtmek değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Özel yığın dökümü ve bir mini döküm Başlat tarafından belirtilen ek verileri dahil belirtir [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri aynı yönteme geçirilen.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Özel yığın dökümü dinamik olarak ayrılmamış tüm çalışma zamanı durumu verileri toplamanız gereken belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Türünde bir parametre `ECustomDumpFlavor` geçirilir [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
