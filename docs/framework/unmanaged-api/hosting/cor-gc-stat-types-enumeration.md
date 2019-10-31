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
ms.openlocfilehash: b0fbc462283ef1577de8100e60fd09caa53db539
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131908"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES Numaralandırması
Çöp toplama için kaydedilecek istatistikleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, [cor_gc_stats](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısındaki hangi Istatistiklerin [ICLRGCManager:: GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi tarafından ayarlanacağını belirtir.  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını kaydeder.|  
|`COR_GC_MEMORYUSAGE`|Bellek kullanımını ve çöp toplama boyutu istatistiklerini kaydeder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COR_GC_STATS Yapısı](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
