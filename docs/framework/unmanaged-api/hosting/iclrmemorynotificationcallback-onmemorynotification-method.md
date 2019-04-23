---
title: ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c7866e0ecc62f037284a5329cb5785be90088f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115849"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a>ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi
Bellek Yükü bilgisayarda ortak dil çalışma zamanı (CLR) bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `eMemoryAvailable`  
 [in] Aşağıdakilerden birini [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) değerleri, bilgisayarın bellek baskısı belirten şu anda karşılaşılan.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnMemoryNotification` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR için bir geri çağırma kaydeder `OnMemoryNotification` bir çağrı kullanılarak [Ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemi. Çalışma zamanı ana bilgisayar kaynakları düşük çalıştırıyorsanız bu bellek bildirdiğinde ek bellek boşaltmak için geri döndürülen bilgileri kullanır.  
  
> [!NOTE]
>  Çağrılar `OnMemoryNotification` hiçbir zaman engellememe. Bunlar her zaman hemen döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [RegisterMemoryNotificationCallback Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [ICLRMemoryNotificationCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
