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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131153"
---
# <a name="econtexttype-enumeration"></a>EContextType Numaralandırması
Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eCurrentContext`|Ortak dil çalışma zamanı (CLR), [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SETSECURITYCONTEXT çağrısında CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir. ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)yöntemi.|  
|`eRestrictedContext`|Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemlerine yapılan çağrılarında bir parametre değeri olarak `EContextType` değerlerinden birini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
