---
description: ': IHostSecurityManager:: SetThreadToken yöntemi hakkında daha fazla bilgi edinin'
title: IHostSecurityManager::SetThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 96fb8d487cecc0e62d9b7787c686c74898d99d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671405"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a>IHostSecurityManager::SetThreadToken Yöntemi

Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `hToken`  
 'ndaki Şu anda yürütülmekte olan iş parçacığı için ayarlanacak belirtecin tanıtıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetThreadToken` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `IHostSecurityManager::SetThreadToken` aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, Win32 işlevi çağıranın rastgele bir iş parçacığına bir tutamacı geçmesine izin verir, ancak `IHostSecurityManager::SetThreadToken` bir belirteci yalnızca şu anda yürütülmekte olan iş parçacığıyla ilişkilendirebilirler.  
  
 `HANDLE`Tür com uyumlu değildir; diğer bir deyişle, boyutu bir işletim sistemine özeldir ve özel sıralama gerektirir. Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
