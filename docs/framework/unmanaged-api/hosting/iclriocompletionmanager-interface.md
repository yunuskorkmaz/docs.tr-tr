---
title: ICLRIoCompletionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: 71afc5e9772f82b922e8f428e6d808e46d092704
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504218"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager Arabirimi
Ana bilgisayarın, belirtilen g/ç isteklerinin durumunun ortak dil çalışma zamanına (CLR) bildirmesini sağlayan bir geri çağırma yöntemi uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[OnComplete Yöntemi](iclriocompletionmanager-oncomplete-method.md)|[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin clr 'ye bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md) arabirimini kullanarak g/ç tamamlama soyutlama uygular. CLR bu arabirim aracılığıyla g/ç istekleri yapar ve ana bilgisayar, bu tür isteklerin çalışma zamanına arabirimini kullanarak bildirir `ICLRIoCompletionManager` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
