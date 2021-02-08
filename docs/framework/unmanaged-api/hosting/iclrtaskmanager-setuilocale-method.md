---
description: ': ICLRTaskManager:: Setuıcale yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: f4fcc916c520489bd1e39f6a44bc1bb971df4bba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799466"
---
# <a name="iclrtaskmanagersetuilocale-method"></a>ICLRTaskManager::SetUILocale Yöntemi

Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `lcid`  
 'ndaki Kullanıcı arabirimi için yeni atanan coğrafi kültür ve dil ile eşleşen yerel ayar tanımlayıcı değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetUILocale` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `SetUILocale` Ana bilgisayarın, yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
