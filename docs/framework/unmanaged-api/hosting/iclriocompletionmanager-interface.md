---
title: ICLRIoCompletionManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99dc183674abaff33047f070c14794150a8615f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager Arabirimi
Implements belirtilen g/ç durumunu ortak dil çalışma zamanı (CLR) bilgilendirmek için ana izin veren bir geri çağırma yöntemi ister.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnComplete Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|CLR yapılan bir çağrı kullanılarak yapılan bir g/ç isteği durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar kullanarak g/ç tamamlama soyutlama uygulayan [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) arabirimi. CLR g/ç istekleri bu arabirimi aracılığıyla yapar ve kullanarak bu tür istekleri sonucunu çalışma zamanı ana bildirir `ICLRIoCompletionManager` arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [IHostThreadPoolManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
