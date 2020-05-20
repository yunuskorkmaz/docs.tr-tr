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
ms.openlocfilehash: ceb68410e808bf7843149e3f05a39c7a98d0c000
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616300"
---
# <a name="econtexttype-enumeration"></a>EContextType Numaralandırması
Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eCurrentContext`|Ortak dil çalışma zamanı (CLR) için [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) metoduna yapılan çağrıda CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir.|  
|`eRestrictedContext`|Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `EContextType` ve yöntemlerine yapılan çağrılarında bir parametre değeri olarak değerlerden birini sağlar `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)
