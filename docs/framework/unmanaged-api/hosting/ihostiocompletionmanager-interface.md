---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager arabirimi'
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
ms.openlocfilehash: 30cb0ecbfd9645bc0374e3570751832d6fa8eced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708326"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager Arabirimi

Ortak dil çalışma zamanının (CLR) konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime girmesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Bind Yöntemi](ihostiocompletionmanager-bind-method.md)|Bir tanıtıcıyı g/ç tamamlama bağlantı noktasına bağlar.|  
|[CloseIoCompletionPort Yöntemi](ihostiocompletionmanager-closeiocompletionport-method.md)|Daha önceki bir çağrısıyla oluşturulmuş bir bağlantı noktasını kapatır `CreateIoCompletionPort` .|  
|[CreateIoCompletionPort Yöntemi](ihostiocompletionmanager-createiocompletionport-method.md)|Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.|  
|[GetAvailableThreads Yöntemi](ihostiocompletionmanager-getavailablethreads-method.md)|Şu anda istek işlemekte olan g/ç Tamamlama iş parçacığı sayısını alır.|  
|[GetHostOverlappedSize Yöntemi](ihostiocompletionmanager-gethostoverlappedsize-method.md)|Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.|  
|[GetMaxThreads Yöntemi](ihostiocompletionmanager-getmaxthreads-method.md)|Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.|  
|[GetMinThreads Yöntemi](ihostiocompletionmanager-getminthreads-method.md)|Hizmetin g/ç isteklerine hizmet vermek için sağladığı en az iş parçacığı sayısını alır.|  
|[InitializeHostOverlapped Yöntemi](ihostiocompletionmanager-initializehostoverlapped-method.md)|Bir g/ç isteğiyle ilgili özel verileri başlatmak için ana bilgisayara bir fırsat sağlar.|  
|[SetCLRIoCompletionManager Yöntemi](ihostiocompletionmanager-setclriocompletionmanager-method.md)|CLR tarafından uygulanan bir [ıclriocompletionmanager](iclriocompletionmanager-interface.md) örneğine yönelik arabirim işaretçisi ile konağa sağlar.|  
|[SetMaxThreads Yöntemi](ihostiocompletionmanager-setmaxthreads-method.md)|Ana bilgisayar tarafından g/ç isteklerine hizmet vermek için ayrılan iş parçacığı sayısı üst sınırını ayarlar.|  
|[SetMinThreads Yöntemi](ihostiocompletionmanager-setminthreads-method.md)|Ana bilgisayarın g/ç tamamlama için en az sayıda iş parçacığı sayısını ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 `IHostIoCompletionManager``ICLRIoCompletionManager`clr tarafından uygulanan arabirime karşılık gelir. CLR, `IHostIoCompletionManager` tutamaçları konağın sağladığı bağlantı noktalarına bağlamak için yöntemini çağırır ve konak `ICLRIoCompletionManager` g/ç isteklerinin tamamlanmasını raporlamak için yöntemlerini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
