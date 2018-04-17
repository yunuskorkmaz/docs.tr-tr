---
title: ICLRSyncManager Arabirimi
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17a1e3073713b54cb7a68e6ba3ef2562d4fbcaeb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager Arabirimi
İstenen görevler hakkında bilgi almak ve kendi eşitleme uygulamasında kilitlenmeleri algılamak için konak izin yöntemleri tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator Yöntemi](iclrsyncmanager-createrwlockowneriterator-method.md)|Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.|  
|[DeleteRWLockOwnerIterator Yöntemi](iclrsyncmanager-deleterwlockowneriterator-method.md)|CLR yapılan bir çağrı tarafından oluşturulan bir yineleyici destroy istekleri `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner Yöntemi](iclrsyncmanager-getmonitorowner-method.md)|Belirtilen İzleyici sahibi görev alır.|  
|[GetRWLockOwnerNext Yöntemi](iclrsyncmanager-getrwlockownernext-method.md)|Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Threading.Thread>  
 [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)  
 [Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [Barındırma Arabirimleri](hosting-interfaces.md)
