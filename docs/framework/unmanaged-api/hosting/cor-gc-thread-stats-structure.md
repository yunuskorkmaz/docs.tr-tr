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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f453867f6b46265fdbf567b4374ddc64b4efe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563905"
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
|`PerThreadAllocation`|Geçerli iş parçacığı üzerinde ayrılmış bellek bayt sayısı `COR_GC_THREAD_STATS` örneği. Bu sayı her zaman sıfır nesil atık toplama işlemi gerçekleştiğinde sıfır olarak temizlenir.|  
|`Flags`|Bayt sayısı, en son çöp toplama daha yüksek bir nesle yükseltilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) çıkış parametresi türü alan `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
