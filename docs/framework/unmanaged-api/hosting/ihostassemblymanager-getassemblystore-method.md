---
title: IHostAssemblyManager::GetAssemblyStore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 91c9a92d83312efcfd90a15aa0a60cccb6b44d7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134731"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a>IHostAssemblyManager::GetAssemblyStore Yöntemi
Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppAssemblyStore`  
 dışı `IHostAssemblyStore` örneğine yönelik bir işlev işaretçisi veya konak `IHostAssemblyStore`uygulamadıysanız null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetAssemblyStore` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOINTERFACE|Ana bilgisayar `IHostAssemblyStore`bir uygulamasını sağlamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostAssemblyStore`, bir konağın CLR 'den bağımsız olarak derlemelere ve modüllere bağlanmasına izin veren yöntemler sağlar. Konaklar genellikle derlemelerin dosya sistemi dışındaki biçimlerden yüklenmesine izin vermek için derleme depoları sağlar.  
  
> [!NOTE]
> Ana bilgisayar `IHostAssemblyStore`uygulamadıysanız, `GetAssemblyStore` bir HRESULT değeri döndürmelidir ve `ppAssemblyStore` null olarak ayarlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
