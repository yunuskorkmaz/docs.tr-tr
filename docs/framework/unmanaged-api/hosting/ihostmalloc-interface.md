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
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441354"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc Arabirimi
Ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden öbek hassas ayırmaları istemesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Ana bilgisayar yığınından istenilen bellek miktarını tahsis istek sayısı.|  
|[DebugAlloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Konak istenilen bellek miktarını yığınından ayırın ve ayrıca burada belleği ayrıldı izlemek ister.|  
|[Free Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Kullanarak ayrılmış bellek boşaltır `Alloc` yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
