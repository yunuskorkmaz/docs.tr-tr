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
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133928"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager Arabirimi
Konağın istenen görevler hakkında bilgi almasını ve eşitleme uygulamasında kilitlenmeleri algılamasını sağlayan yöntemleri tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator Yöntemi](iclrsyncmanager-createrwlockowneriterator-method.md)|Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.|  
|[DeleteRWLockOwnerIterator Yöntemi](iclrsyncmanager-deleterwlockowneriterator-method.md)|CLR 'nin `CreateRWLockOwnerIterator`çağrısı tarafından oluşturulan bir yineleyiciyi yok ettiğini ister.|  
|[GetMonitorOwner Yöntemi](iclrsyncmanager-getmonitorowner-method.md)|Belirtilen izleyicinin sahibi olan görevi alır.|  
|[GetRWLockOwnerNext Yöntemi](iclrsyncmanager-getrwlockownernext-method.md)|Geçerli okuyucu-yazıcı kilidinde bekleyen bir sonraki görevi alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
- [Yönetilen ve yönetilmeyen Iş parçacığı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Barındırma Arabirimleri](hosting-interfaces.md)
