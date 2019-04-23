---
title: EContextType Numaralandırması
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3643bf4880532a46fe7f9f57b8077032013728
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118085"
---
# <a name="econtexttype-enumeration"></a>EContextType Numaralandırması
Güvenlik bağlamı şu anda yürütülen iş parçacığının açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eCurrentContext`|Ortak dil çalışma zamanı (CLR) çağıran sırada geçerli iş parçacığının içeriğine gösterir [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) yöntemi veya bir çağrıda CLR tarafından talep edilen içeriği [ Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) yöntemi.|  
|`eRestrictedContext`|Ana bilgisayar çöp Toplayıcıya veya sınıf veya modül oluşturucuları gibi daha düşük ayrıcalıklara sahip bir bağlam gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR birini sağlayan `EContextType` değerleri yapılan çağrıda bir parametre değeri olarak `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
