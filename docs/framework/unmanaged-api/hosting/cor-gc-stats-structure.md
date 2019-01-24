---
title: COR_GC_STATS Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fc212321b28545f62f0a1c2965281d02ac73e40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638112"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS Yapısı
Ortak dil çalışma zamanı (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`Flags`|Hangi alan değerlerini hesaplanır ve döndürülen gösterir.|  
|`ExplicitGCCount`|Dış istek tarafından zorlanan çöp koleksiyonları sayısını gösterir.|  
|`GenCollectionsTaken`|Her bir oluşturmada gerçekleştirilen çöp koleksiyonları sayısını gösterir.|  
|`CommittedKBytes`|Tüm yığınlara kaydedilen kilobayt sayısı.|  
|`ReservedKBytes`|Tüm yığınlara ayrılmış kilobayt sayısı.|  
|`Gen0HeapSizeKBytes`|Nesil sıfır yığın kilobayt cinsinden boyutu.|  
|`Gen1HeapSizeKBytes`|Oluşturma bir yığın kilobayt cinsinden boyutu.|  
|`Gen2HeapSizeKBytes`|Nesil iki yığın kilobayt cinsinden boyutu.|  
|`LargeObjectHeapSizeKBytes`|Büyük nesne yığının kilobayt cinsinden boyutu.|  
|`KBytesPromotedFromGen0`|Oluşturma bir sıfır kuşaktan yükseltilen nesnelerin kilobayt cinsinden boyutu.|  
|`KBytesPromotedFromGen1`|Oluşturma bir nesle iki yükseltilir nesnelerin kilobayt cinsinden boyutu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) gerektirdiğine `Flags` alanını `COR_GC_STATS` yapısı bir veya daha fazla değere ayarlanacak [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) belirtmek için sabit listesi Ayarlanacak istatistikleri şunlardır.  
  
 Aşağıdaki tabloda bu yapı için iki tarafından sağlanan istatistikleri eşler [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değerlerinin `COR_GC_COUNTS` ve `COR_GC_MEMORYUSAGE`.  
  
|COR_GC_COUNTS tarafından belirtilen|COR_GC_MEMORYUSAGE tarafından belirtilen|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Kullanım örneği aşağıdaki gibidir:  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)
- [Atık Toplama](../../../../docs/standard/garbage-collection/index.md)
