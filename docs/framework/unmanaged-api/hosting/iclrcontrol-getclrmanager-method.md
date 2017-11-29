---
title: ICLRControl::GetCLRManager Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.GetCLRManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dc6f707511f9d6f4883aecbd2a26a587a902c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager Metodu
Arabirim işaretçisi herhangi bir ana bilgisayar ortak dil çalışma zamanı (CLR) yapılandırmak için kullanabileceğiniz Yöneticisi türü örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `riid`  
 [in] `IID` Döndürülecek Yöneticisi türü. Aşağıdaki `IID` değerler desteklenir.  
  
-   IID_ICLRDebugManager: belirleyen `ppObject` türünün [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).  
  
-   IID_ICLRErrorReportingManager: belirleyen `ppObject` türünün [Iclrerrorreportingmanager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).  
  
-   IID_ICLRGCManager: belirleyen `ppObject` türünün [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
-   IID_ICLRHostProtectionManager: belirleyen `ppObject` türünün [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).  
  
-   IID_ICLROnEventManager: belirleyen `ppObject` türünün [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).  
  
-   IID_ICLRPolicyManager: belirleyen `ppObject` türünün [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).  
  
-   IID_ICLRTaskManager: speciries, `ppObject` türünün [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).  
  
 `ppObject`  
 [out] Arabirim işaretçisi istenen Yöneticisi ya da geçersiz Yöneticisi türü istendi yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOINTERFACE|Arabirim türü desteklenmiyor.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
