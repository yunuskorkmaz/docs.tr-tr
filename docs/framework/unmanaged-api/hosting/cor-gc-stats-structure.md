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
ms.openlocfilehash: 12c00ed009e0e57436a71aed256b07a58ba68a32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138344"
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
|`Flags`|Hangi alan değerlerinin hesaplanacağını ve döndürüleceğini belirtir.|  
|`ExplicitGCCount`|Dış istek tarafından zorlanan çöp koleksiyonlarının sayısını belirtir.|  
|`GenCollectionsTaken`|Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını belirtir.|  
|`CommittedKBytes`|Tüm yığınlara kaydedilen kilobayt toplam sayısı.|  
|`ReservedKBytes`|Tüm yığınlara ayrılan toplam kilobayt sayısı.|  
|`Gen0HeapSizeKBytes`|Kuşak sıfır yığınının kilobayt cinsinden boyutu.|  
|`Gen1HeapSizeKBytes`|Kuşak-tek yığının kilobayt cinsinden boyutu.|  
|`Gen2HeapSizeKBytes`|Oluşturma-iki yığının kilobayt cinsinden boyutu.|  
|`LargeObjectHeapSizeKBytes`|Büyük nesne yığınının kilobayt cinsinden boyutu.|  
|`KBytesPromotedFromGen0`|Sıfırdan yükseltilen nesnelerin kilobayt cinsinden boyutu. kuşak.|  
|`KBytesPromotedFromGen1`|Tek nesil bir oluşturma işleminden yükseltilen nesnelerin kilobayt cinsinden boyutu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRGCManager:: GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi, hangi istatistiklerin ayarlanacağını belirlemek için `COR_GC_STATS` yapısının `Flags` alanının bir veya daha fazla [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırması değerine ayarlanmasını gerektirir.  
  
 Aşağıdaki tabloda, bu yapı tarafından sunulan istatistikler iki [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) sabit listesi değeri, `COR_GC_COUNTS` ve `COR_GC_MEMORYUSAGE`eşlenir.  
  
|COR_GC_COUNTS tarafından belirtilen|COR_GC_MEMORYUSAGE tarafından belirtilen|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Kullanım örneği aşağıdaki gibidir:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Otomatik Bellek Yönetimi](../../../standard/automatic-memory-management.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)
