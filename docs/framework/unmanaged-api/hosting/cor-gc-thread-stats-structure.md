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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616703"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS Yapısı
Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`PerThreadAllocation`|Geçerli örnekle ilişkili iş parçacığı üzerinde ayrılan bellek bayt sayısı `COR_GC_THREAD_STATS` . Her nesil sıfır atık toplama gerçekleştiğinde bu sayı sıfır olarak temizlenir.|  
|`Flags`|En son atık toplamada daha yüksek bir oluşturmaya yükseltilen bayt sayısı.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) , türünde bir çıkış parametresi alır `COR_GC_THREAD_STATS` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
