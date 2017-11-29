---
title: IHostMalloc Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a>IHostMalloc Arabirimi
Ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden öbek hassas ayırmaları istemesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Ana bilgisayar yığınından istenilen bellek miktarını tahsis istek sayısı.|  
|[DebugAlloc yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Konak istenilen bellek miktarını yığınından ayırın ve ayrıca burada belleği ayrıldı izlemek ister.|  
|[Free yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Kullanarak ayrılmış bellek boşaltır `Alloc` yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir arabirim işaretçisi alır bir `IHostMalloc` çağırarak örneği [Ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihostmemorymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
