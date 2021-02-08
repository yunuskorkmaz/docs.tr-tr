---
description: ': ICLRTaskManager:: SetLocale Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 401f227f900ab4b89cd6fc5b7902b4314a7687e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799487"
---
# <a name="iclrtaskmanagersetlocale-method"></a>ICLRTaskManager::SetLocale Yöntemi

Ana bilgisayarın şu anda yürütülmekte olan görevde yerel ayar tanımlayıcısının (coğrafi kültür ve dille eşlenir) değerini değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `lcid`  
 'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `SetLocale` Ana bilgisayara, yerel ayarların eşitlenmesi için sahip olabileceği mekanizmaların yürütülmesi için bir fırsat sağlar.  
  
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
