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
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493429"
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
  
|Üye|Description|  
|------------|-----------------|  
|`eCurrentContext`|Ortak dil çalışma zamanı (CLR) için [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) metoduna yapılan çağrıda CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir.|  
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
