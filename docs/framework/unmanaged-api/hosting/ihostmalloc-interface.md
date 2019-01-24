---
title: IHostMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea3656fa00e84291ff7b2bdb65f9300cd7933c0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571788"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc Arabirimi
Ortak dil çalışma zamanı (CLR) yığın konağı üzerinden hassas ayırmaları istemesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|İstekleri konak yığından istenen bellek miktarı ayırın.|  
|[DebugAlloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Konak istenilen bellek miktarını yığından ayırmak ve ayrıca bellek ayrıldığı izlemek ister.|  
|[Free Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Kullanarak ayrılan bellek serbest bırakma `Alloc` yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
