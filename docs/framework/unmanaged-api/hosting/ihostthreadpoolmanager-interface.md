---
title: IHostThreadPoolManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2773042c695320ab1e90d4c5d341e2df5f0f778f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager Arabirimi
Ortak dil çalışma zamanı (CLR) iş parçacığı havuzu yapılandırmak için ve iş parçacığı havuzu iş öğelerine kuyruğuna sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAvailableThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|İş öğeleri şu anda işlenmiyor iş parçacığı havuzundaki iş parçacığı sayısını alır.|  
|[GetMaxThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Konak tutar iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.|  
|[GetMinThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Ana bilgisayar tutar boş iş parçacığı en az sayıda istekleri kapatıldığını içinde alır.|  
|[QueueUserWorkItem yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Bir işlev yürütme için sıraya koyar ve işlev tarafından kullanılacak verilerini içeren bir nesne sağlar.|  
|[SetMaxThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.|  
|[SetMinThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Konak korumalıdır boş iş parçacığı sayısı alt sınırını istekleri kapatıldığını içinde ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar çağrıları belirtilen değerleri kullanarak iş parçacığı havuzu yapılandırmak için gerekli olmayan `SetMaxThreads` ve `SetMinThreads` yöntemleri. Bu durumda, ana bilgisayar bu yöntemlerden E_NOTIMPL HRESULT değerini döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
