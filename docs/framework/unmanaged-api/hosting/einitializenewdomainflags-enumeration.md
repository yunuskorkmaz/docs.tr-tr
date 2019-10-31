---
title: EInitializeNewDomainFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129416"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags Numaralandırması
Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Bayrak yok.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Ana bilgisayarın <xref:System.AppDomainManager.InitializeNewDomain%2A> yönteminde uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı ortak dil çalışma zamanına (CLR) bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRDomainManager:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi, `EInitializeNewDomainFlags`türünde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [SetAppDomainManagerType Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
