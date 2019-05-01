---
title: IGCThreadControl Arabirimi
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992777"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl Arabirimi
Bir çöp toplama işlemi için normalde engellenecek iş parçacıklarını zamanlama katılım için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SuspensionEnding Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|Konak, çalışma zamanı iş parçacıklarının çöp toplama ya da diğer ertelenmesi sonra sürdürülmekte bildirir.|  
|[SuspensionStarting Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|Konak, çalışma zamanının çöp toplama için bir iş parçacığını askıya alma ya da diğer ertelenmesi başlıyor bildirir.|  
|[ThreadIsBlockingForSuspension Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|Konak, çağrıyı yapan iş parçacığının yaklaşık, belki de bir çöp toplama ya da diğer ertelenmesi için engellemek için olduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
