---
title: IHostSecurityManager::OpenThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176272"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken Yöntemi
Şu anda çalıştırılamakta olan iş parçacığıyla ilişkili isteğe bağlı erişim belirteci açılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwDesiredAccess`  
 [içinde] İş parçacığı belirteci için istenen erişim türlerini belirten erişim değerleri maskesi. Bu değerler Win32 `OpenThreadToken` işlevinde tanımlanır. İstenen erişim türleri, hangi erişim türlerinin hibe veya reddedildiğini belirlemek için belirteci isteğe bağlı erişim denetim listesine (DACL) göre uzlaştırılır.  
  
 `bOpenAsSelf`  
 [içinde] `true` erişim denetiminin arama iş parçacığı için işlemin güvenlik bağlamı kullanılarak yapılması gerektiğini belirtmek için; `false` erişim denetiminin arama iş parçacığının kendisi için güvenlik bağlamı kullanılarak gerçekleştirilmesi gerektiğini belirtmek için. İş parçacığı istemci nin kimliğine bürünüyorsa, güvenlik bağlamı istemci işlemine ait olabilir.  
  
 `phThreadToken`  
 [çıkış] Yeni açılan erişim belirteci için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostSecurityManager::OpenThreadToken`Win32 işlevi, arayan kişinin bir tutamaç içinde rasgele bir iş parçacığına geçmesine izin verir, ancak `IHostSecurityManager::OpenThreadToken` yalnızca arama iş parçacığı ile ilişkili belirteci açar.  
  
 Tür `HANDLE` COM uyumlu değildir, yani boyutu işletim sistemine özgüdür ve özel mareşalleme gerektirir. Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ve ana bilgisayar arasında kullanım içindir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
