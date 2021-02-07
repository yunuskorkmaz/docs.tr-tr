---
description: 'Daha fazla bilgi edinin: IHostGCManager Interface'
title: IHostGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: da229c04eb5f5a27c34c133b5c88183d00f47c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708664"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager Arabirimi

Ortak dil çalışma zamanı (CLR) tarafından uygulanan çöp toplama mekanizmasında olayların ana bilgisayarına bildirimde bulunan yöntemler sağlar.  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|[SuspensionEnding Yöntemi](ihostgcmanager-suspensionending-method.md)|Konağa CLR 'nin bir çöp toplama işlemi için askıya alınmış iş parçacıklarında görevlerin yürütülmesini sürdürmesinin sürdürüyor olduğunu bildirir.|  
|[SuspensionStarting Yöntemi](ihostgcmanager-suspensionstarting-method.md)|Bir atık toplama işlemi gerçekleştirmek için, CLR 'nin görevlerin yürütülmesini askıya aldığı konağa bildirir.|  
|[ThreadIsBlockingForSuspension Yöntemi](ihostgcmanager-threadisblockingforsuspension-method.md)|Ana bilgisayara, yöntem çağrısının yaptığı iş parçacığının çöp toplama için engellemek üzere olduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
