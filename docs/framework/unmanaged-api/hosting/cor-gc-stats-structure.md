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
ms.openlocfilehash: 009f1482de6e1daea21766300b4fb6a3ab0ffc8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432294"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS Yapısı
Ortak dil çalışma zamanı (CLR) atık toplama mekanizmasını ilgili istatistikler sağlar.  
  
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
|`ExplicitGCCount`|Dış istek tarafından zorlanan çöp koleksiyonlarının sayısını gösterir.|  
|`GenCollectionsTaken`|Her oluşturulmasında gerçekleştirilen çöp koleksiyonlarının sayısını gösterir.|  
|`CommittedKBytes`|Tüm yığın kaydedilen kilobayt toplam sayısı.|  
|`ReservedKBytes`|Tüm yığın ayrılmış kilobayt toplam sayısı.|  
|`Gen0HeapSizeKBytes`|Kilobayt cinsinden nesil sıfır yığın boyutu.|  
|`Gen1HeapSizeKBytes`|Kilobayt cinsinden oluşturma-bir yığın boyutu.|  
|`Gen2HeapSizeKBytes`|Kilobayt cinsinden nesil iki yığın boyutu.|  
|`LargeObjectHeapSizeKBytes`|Kilobayt cinsinden büyük nesne yığın boyutu.|  
|`KBytesPromotedFromGen0`|Nesil biri sıfır kuşaktan yükseltilen nesnelerin kilobayt cinsinden boyutu.|  
|`KBytesPromotedFromGen1`|Nesil iki kuşaktan bir yükseltilmiş nesnelerin kilobayt cinsinden boyutu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) gerektirdiğine `Flags` alanını `COR_GC_STATS` yapısı bir veya daha fazla değerlere ayarlamak için [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) belirtmek için numaralandırması İstatistikleri ayarlanması üzeresiniz.  
  
 Aşağıdaki tabloda bu iki yapısına tarafından sağlanan istatistikleri eşleyen [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değerlerinin `COR_GC_COUNTS` ve `COR_GC_MEMORYUSAGE`.  
  
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
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** GCHost.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)  
 [Atık Toplama](../../../../docs/standard/garbage-collection/index.md)
