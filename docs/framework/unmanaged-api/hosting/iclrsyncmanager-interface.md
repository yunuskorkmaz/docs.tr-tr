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
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203099"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
- [Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Barındırma Arabirimleri](hosting-interfaces.md)
