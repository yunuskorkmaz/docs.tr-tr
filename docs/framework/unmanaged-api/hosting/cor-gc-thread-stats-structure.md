---
title: COR_GC_THREAD_STATS Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178262"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS Yapısı
Çöp toplamayla ilgili iş parçacığı başına istatistikleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`PerThreadAllocation`|Geçerli `COR_GC_THREAD_STATS` örnekle ilişkili iş parçacığına ayrılan bellek baytlarının sayısı. Bu sayı, her nesil-sıfır çöp toplama oluştuğunda sıfıra temizlenir.|  
|`Flags`|En son çöp toplama da daha yüksek bir nesle yükseltilen bayt sayısı.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) türünden `COR_GC_THREAD_STATS`bir çıkış parametresi alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** GCHost.idl  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
