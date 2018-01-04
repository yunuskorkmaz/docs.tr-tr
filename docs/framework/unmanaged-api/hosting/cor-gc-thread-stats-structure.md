---
title: "COR_GC_THREAD_STATS Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266352984cf50dc906e77598e8dcc9216526ce17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS Yapısı
Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`PerThreadAllocation`|Geçerli ilişkili iş parçacığında ayrılan belleği bayt sayısı `COR_GC_THREAD_STATS` örneği. Bu sayı sıfıra nesil sıfır çöp toplama her gerçekleştiğinde temizlenir.|  
|`Flags`|Bayt sayısı, en son çöp toplama için daha yüksek kuşaklı yükseltildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) bir çıktı parametresi türü alan `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** GCHost.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
