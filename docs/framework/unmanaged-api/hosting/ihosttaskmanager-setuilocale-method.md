---
title: IHostTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132939"
---
# <a name="ihosttaskmanagersetuilocale-method"></a>IHostTaskManager::SetUILocale Yöntemi
Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiğinizi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lcid`  
 'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetUILocale` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOTIMPL|Konak, yönetilen kullanıcı kodunun UI kültürünü değiştirmesine izin vermez.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğinin değeri yönetilen kodla değiştirildiğinde, çalışma zamanı `SetUILocale` çağırır. Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar. Bir konak, Kullanıcı arabirimi yerel ayarının yönetilen koddan değiştirilmesine izin vermezse veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [SetLocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
