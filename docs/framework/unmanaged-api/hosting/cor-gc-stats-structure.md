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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176532"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS Yapısı
Ortak dil çalışma zamanının (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`Flags`|Hangi alan değerlerinin hesaplanıp döndürülmesi gerektiğini gösterir.|  
|`ExplicitGCCount`|Dış istek tarafından zorlanan çöp toplama sayısını gösterir.|  
|`GenCollectionsTaken`|Her nesil için gerçekleştirilen çöp toplama sayısını gösterir.|  
|`CommittedKBytes`|Tüm yığınlarda işlenen toplam kilobayt sayısı.|  
|`ReservedKBytes`|Tüm yığınlarda ayrılmış toplam kilobayt sayısı.|  
|`Gen0HeapSizeKBytes`|Kilobaytlıklarda, sıfır kuşağının büyüklüğü.|  
|`Gen1HeapSizeKBytes`|Kilobaytlıklarda, nesil-bir yığının büyüklüğü.|  
|`Gen2HeapSizeKBytes`|Kilobaytlıkboyutu, nesil-iki yığın.|  
|`LargeObjectHeapSizeKBytes`|Büyük nesne yığınının büyüklüğü, kilobaytlar halinde.|  
|`KBytesPromotedFromGen0`|Kilobaytlarda, sıfır kuşağından nesil bire yükseltilen nesnelerin boyutu.|  
|`KBytesPromotedFromGen1`|Kilobaytlarda, birinci nesilden ikinci nesile terfi eden nesnelerin boyutu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi, `Flags` hangi istatistiklerin ayarlaneceğini belirtmek için `COR_GC_STATS` yapıalanının [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırmanın bir veya daha fazla değerine ayarlanmasını gerektirir.  
  
 Aşağıdaki tablo, bu yapı tarafından sağlanan istatistikleri iki [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değeri `COR_GC_COUNTS` ile eşler ve. `COR_GC_MEMORYUSAGE`  
  
|COR_GC_COUNTS tarafından belirtilir|COR_GC_MEMORYUSAGE tarafından belirtilir|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Kullanıma bir örnek aşağıdaki gibidir:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** GCHost.idl  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Otomatik Bellek Yönetimi](../../../standard/automatic-memory-management.md)
- [Çöp Toplama](../../../standard/garbage-collection/index.md)
