---
title: "ICLRGCManager::SetGCStartupLimits Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fd5a1135866b75ea1d11fc5a14289104edfeac4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>ICLRGCManager::SetGCStartupLimits Yöntemi
Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kesim boyutu ayarlayabilir ve en fazla kuşak 0 boyutuna büyük değerler `DWORD` kullanarak [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `SegmentSize`  
 [in] Çöp toplama kesim belirtilen boyutu.  
  
 Minimum kesim boyutu 4 MB'tır. Kesimleri artan aralıklarla 1 MB veya daha büyük olabilir.  
  
 `MaxGen0Size`  
 [in] 0 oluşturma için belirtilen en büyük boyutu.  
  
 Minimum kuşak 0 boyutu 64 KB'tır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Değerleri, `SetGCStartupLimits` kümeleri yalnızca bir kez belirtilebilir. Daha sonra çağrılar `SetGCStartupLimits` göz ardı edilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)  
 [Atık Toplama](../../../../docs/standard/garbage-collection/index.md)  
 [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRGCManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
