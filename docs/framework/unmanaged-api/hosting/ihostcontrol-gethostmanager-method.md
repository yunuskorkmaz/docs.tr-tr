---
title: IHostControl::GetHostManager Metodu
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 355d2e259adb13da44b09e19872337c17ac20ade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439328"
---
# <a name="ihostcontrolgethostmanager-method"></a>IHostControl::GetHostManager Metodu
Arabirim işaretçisi arabirimi ana bilgisayarın uygulaması için belirtilen alır `IID`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `riid`  
 [in] `IID` Ortak dil çalışma zamanı (CLR) için sorgulama arabirimi.  
  
 `ppObject`  
 [out] Ana bilgisayar uygulanan arabirimi ya da ana bilgisayar bu arabirim desteklemiyorsa null işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetHostManager` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|İstenen `IID` geçerli değil.|  
|E_NOINTERFACE|İstenen arabirimi desteklemiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir veya daha fazla aşağıdaki arabirimleri destekleyip desteklemediğini belirlemek için ana sorgular:  
  
-   [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [Ihostthreadpoolmanager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [Ihostsyncmanager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [Ihostassemblymanager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [Ihostgcmanager](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [Ihostpolicymanager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 Konak belirtilen arabirim destekliyorsa, ayarlar `ppObject` bu arabirimin uygulaması için. Aksi takdirde, ayarlar `ppObject` null.  
  
 CLR çağrılmayan `Release` bile, kapattığınızda konak yöneticilere.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
