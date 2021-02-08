---
description: 'Daha fazla bilgi edinin: IHostTask arabirimi'
title: IHostTask Arabirimi
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: c46bbdd2e881c20d1ffd634bec8ddfa3b70b0f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784671"
---
# <a name="ihosttask-interface"></a>IHostTask Arabirimi

Ortak dil çalışma zamanının (CLR) görevleri yönetmek için konakla iletişim kurmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alert Yöntemi](ihosttask-alert-method.md)|Konağın geçerli örnek tarafından temsil ettiği görevi `IHostTask` uyandırmasını, bu nedenle görevin iptal edileceğini ister.|  
|[GetPriority Yöntemi](ihosttask-getpriority-method.md)|Geçerli örnek tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır `IHostTask` .|  
|[Join Yöntemi](ihosttask-join-method.md)|Geçerli örnek tarafından temsil edilen görev `IHostTask` tamamlanana kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](ihosttask-alert-method.md) çağrıldığında çağıran görevi engeller.|  
|[SetCLRTask Yöntemi](ihosttask-setclrtask-method.md)|Bir [ICLRTask arabirimi](iclrtask-interface.md) örneğini geçerli `IHostTask` örnekle ilişkilendirir.|  
|[SetPriority Yöntemi](ihosttask-setpriority-method.md)|Konağın, geçerli örnek tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister `IHostTask` .|  
|[Start yöntemi](ihosttask-start-method.md)|Konağın geçerli örnek tarafından temsil edilen görevi `IHostTask` askıya alınmış bir durumdan canlı duruma taşımasını ister, bu da kodun yürütülebileceğini.|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR, `IHostTask` bir görevi başlatmak, iş parçacığı öncelik düzeyini ayarlamak ve daha fazlasını yapmak için tarafından tanımlanan yöntemleri çağırır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
