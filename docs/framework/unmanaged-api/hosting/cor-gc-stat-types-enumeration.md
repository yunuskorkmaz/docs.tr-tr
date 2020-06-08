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
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501709"
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
 Bu numaralandırma, [cor_gc_stats](cor-gc-stats-structure.md) yapısındaki hangi Istatistiklerin [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) yöntemi tarafından ayarlanacağını belirtir.  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını kaydeder.|  
|`COR_GC_MEMORYUSAGE`|Bellek kullanımını ve çöp toplama boyutu istatistiklerini kaydeder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COR_GC_STATS Yapısı](cor-gc-stats-structure.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)
