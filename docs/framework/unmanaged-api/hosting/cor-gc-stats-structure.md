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
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501670"
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
  
|Üye|Description|  
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
 [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) yöntemi, `Flags` `COR_GC_STATS` hangi istatistiklerin ayarlanacağını belirlemek için yapının alanının [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırmasının bir veya daha fazla değerine ayarlanmasını gerektirir.  
  
 Aşağıdaki tabloda, bu yapı tarafından sunulan istatistikler iki [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırma değeri `COR_GC_COUNTS` ve ile eşlenir `COR_GC_MEMORYUSAGE` .  
  
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
