---
title: IHostSecurityManager::GetSecurityContext Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176259"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a>IHostSecurityManager::GetSecurityContext Yöntemi
İstenen [IHostSecurityContext'ı](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) ana bilgisayardan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `eContextType`  
 [içinde] Ne tür bir güvenlik bağlamının döndürüleceklerini belirten [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) değerlerinden biri.  
  
 `ppSecurityContext`  
 [çıkış] Bir arabirim işaretçisinin `IHostSecurityContext` `eContextType`adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetSecurityContext`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar, iş parçacığı belirteçlerine tüm kod erişimini hem CLR hem de kullanıcı kodu yla denetleyebilir. Ayrıca, tam güvenlik bağlamı bilgilerinin eşzamanlı işlemler veya sınırlı kod erişimine sahip kod noktaları arasında aktarılmasını da sağlayabilir. `IHostSecurityContext`CLR'ye opak olan bu güvenlik bağlamı bilgilerini saklar. CLR bu bilgileri yakalar ve iş parçacığı havuzu alt öğe gönderme, sonlandırıcı yürütme ve modül ve sınıf yapısı arasında taşır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EContextType Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
