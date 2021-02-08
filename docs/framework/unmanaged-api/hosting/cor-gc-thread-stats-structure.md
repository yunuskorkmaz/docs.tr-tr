---
description: 'Daha fazla bilgi edinin: COR_GC_THREAD_STATS yapısı'
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
ms.openlocfilehash: 179eb335e9f8c118ee98d4b777c347f3758ee0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799791"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS Yapısı

Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`PerThreadAllocation`|Geçerli örnekle ilişkili iş parçacığı üzerinde ayrılan bellek bayt sayısı `COR_GC_THREAD_STATS` . Her nesil sıfır atık toplama gerçekleştiğinde bu sayı sıfır olarak temizlenir.|  
|`Flags`|En son atık toplamada daha yüksek bir oluşturmaya yükseltilen bayt sayısı.|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) , türünde bir çıkış parametresi alır `COR_GC_THREAD_STATS` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
