---
title: IHostThreadPoolManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fc0a271a9c62406d2942f387a5458e21211116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522732"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager Arabirimi
Ortak dil çalışma zamanı (CLR) iş parçacığı havuzu yapılandırmak ve iş parçacığı havuzu iş öğelerine kuyruğuna olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAvailableThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|İş öğeleri şu anda işleme değil iş parçacığı havuzundaki iş parçacığı sayısını alır.|  
|[GetMaxThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Konak tutan iş parçacığı sayısı, iş parçacığı havuzundaki eşzamanlı olarak alır.|  
|[GetMinThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|En az sayıda konak tutar boşta iş parçacıkları istekleri olasılığına alır.|  
|[QueueUserWorkItem Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Bir işlev yürütme için sıralar ve işlev tarafından kullanılan veri içeren bir nesne sağlar.|  
|[SetMaxThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Ana iş parçacığı havuzundaki koruyabilirsiniz iş parçacığı sayısını ayarlar.|  
|[SetMinThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|En az sayıda konak korumalıdır boşta iş parçacıkları istekleri olasılığına ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana iş parçacığı havuzu yapılan çağrıda belirtilen değerleri kullanarak yapılandırmak için gerekli değildir `SetMaxThreads` ve `SetMinThreads` yöntemleri. Bu durumda, konak, bu yöntemlerden E_NOTIMPL bir HRESULT değerini döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
