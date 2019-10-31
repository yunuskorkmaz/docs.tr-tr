---
title: IHostIoCompletionManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133857"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager Arabirimi
Ortak dil çalışma zamanının (CLR) konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime girmesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Bind Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Bir tanıtıcıyı g/ç tamamlama bağlantı noktasına bağlar.|  
|[CloseIoCompletionPort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Daha önceki bir `CreateIoCompletionPort`çağrısıyla oluşturulmuş bir bağlantı noktasını kapatır.|  
|[CreateIoCompletionPort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.|  
|[GetAvailableThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Şu anda istek işlemekte olan g/ç Tamamlama iş parçacığı sayısını alır.|  
|[GetHostOverlappedSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.|  
|[GetMaxThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.|  
|[GetMinThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Hizmetin g/ç isteklerine hizmet vermek için sağladığı en az iş parçacığı sayısını alır.|  
|[InitializeHostOverlapped Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Bir g/ç isteğiyle ilgili özel verileri başlatmak için ana bilgisayara bir fırsat sağlar.|  
|[SetCLRIoCompletionManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|CLR tarafından uygulanan bir [ıclriocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) örneğine yönelik arabirim işaretçisi ile konağa sağlar.|  
|[SetMaxThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Ana bilgisayar tarafından g/ç isteklerine hizmet vermek için ayrılan iş parçacığı sayısı üst sınırını ayarlar.|  
|[SetMinThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostIoCompletionManager`, CLR tarafından uygulanan `ICLRIoCompletionManager` arabirimine karşılık gelir. CLR, tutamaçları konağın sağladığı bağlantı noktalarına bağlamak için `IHostIoCompletionManager` yöntemlerini çağırır ve konak g/ç isteklerinin tamamlanmasını raporlamak için `ICLRIoCompletionManager` yöntemlerini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
