---
title: ICLRSyncManager Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: ede896cdb93217fcfba9d66ed7102bcc1ba762e9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129330"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager Arabirimi
İstenilen görevler hakkında bilgi almak ve kilitlenmeleri eşitleme uygulanması algılamak için konak izin verme yöntemleri tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator Yöntemi](iclrsyncmanager-createrwlockowneriterator-method.md)|Ortak dil çalışma zamanı (CLR) Okuyucu-Yazıcı kilit Bekleyen görevler kümesini belirlemek için kullanılacak ana bilgisayar için bir yineleyici oluşturma isteği.|  
|[DeleteRWLockOwnerIterator Yöntemi](iclrsyncmanager-deleterwlockowneriterator-method.md)|CLR bir çağrı tarafından oluşturulan bir yineleyici yok istekleri `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner Yöntemi](iclrsyncmanager-getmonitorowner-method.md)|Belirtilen İzleyici sahip görev alır.|  
|[GetRWLockOwnerNext Yöntemi](iclrsyncmanager-getrwlockownernext-method.md)|Geçerli Okuyucu-Yazıcı kilidi beklerken sonraki görev alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)  
 [Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))  
 [Barındırma Arabirimleri](hosting-interfaces.md)
