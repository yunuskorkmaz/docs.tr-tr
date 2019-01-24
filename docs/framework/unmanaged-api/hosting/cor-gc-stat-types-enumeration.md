---
title: COR_GC_STAT_TYPES Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd12feb47352d9bb78aa8ef056072f9bdc6fba3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710332"
---
# <a name="corgcstattypes-enumeration"></a>COR_GC_STAT_TYPES Numaralandırması
Bir çöp toplama için kaydedilecek istatistikleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, hangi istatistikleri belirtir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısı olan ayarlanması [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi.  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Kayıtları atık toplamaları sayısı için her bir oluşturmada gerçekleştirdi.|  
|`COR_GC_MEMORYUSAGE`|Kayıtları bellek kullanımı ve çöp toplama boyutu istatistikleri.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl, GCHost.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [COR_GC_STATS Yapısı](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
