---
title: ICLROnEventManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7486a094deab16ebbc05f19f1b652126479ce11c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638586"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager Arabirimi
Kaydetme ve geri çağırmaları ortak dil çalışma zamanı (CLR) olaylarını kaydını silmek konak sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[RegisterActionOnEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Bir geri çağırma işaretçi belirtilen olay için kaydeder.|  
|[UnregisterActionOnEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Belirtilen olay önceden kaydedilmiş bir geri çağırma işaretçi kaydını siler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar kaydetme ve olay geri çağırmaları kaydını silmek için bir başvuru edinir `ICLROnEventManager` çağırarak [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.  
  
> [!NOTE]
>  Tarafından tanımlanan olayları [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıkları ve birden çok kez tetiklendi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrEvent Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
