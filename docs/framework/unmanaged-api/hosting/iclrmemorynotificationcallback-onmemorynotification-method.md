---
title: "ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651dcd6380702a392d2dd06cf899ea567b004ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a>ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi
Ortak dil çalışma zamanı (CLR) bilgisayardaki Bellek Yükü bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `eMemoryAvailable`  
 [in] Aşağıdakilerden birini [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) değerleri, bellek baskısı bilgisayar belirten şu anda karşılaşılan.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnMemoryNotification`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR için bir geri çağırma kaydeder `OnMemoryNotification` yapılan bir çağrı kullanılarak [Ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemi. Çalışma zamanı ana bilgisayarın bu bellek kaynakları düşük çalıştıran bildirdiğinde ek bellek boşaltmak için geri döndürülen bilgileri kullanır.  
  
> [!NOTE]
>  Çağrılar `OnMemoryNotification` hiçbir zaman engelleyin. Bunlar her zaman hemen döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [RegisterMemoryNotificationCallback Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [ICLRMemoryNotificationCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
