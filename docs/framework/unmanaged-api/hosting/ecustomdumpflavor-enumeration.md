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
ms.openlocfilehash: 2be9f112d5997ec8a6b126229eb8608eb8dd8520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627648"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor Numaralandırması
Hataları bildirirken hangi öğelerin bir yığının özel alt kümesinde içerecek şekilde dökümü gösteren değerleri içerir.  
  
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
|`DUMP_FLAVOR_Mini`|Özel yığının döküm ve bir mini döküm Başlat tarafından belirtilen ek verileri dahil etmek belirtir [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri aynı yönteme geçirilen.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Özel yığının döküm dinamik olarak ayrılmamış tüm çalışma zamanı durumu verilerini toplamanız gereken belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Türünde bir parametre `ECustomDumpFlavor` geçirilir [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
