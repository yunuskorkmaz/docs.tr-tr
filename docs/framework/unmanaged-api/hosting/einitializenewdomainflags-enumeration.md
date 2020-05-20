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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616235"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags Numaralandırması
Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`eInitializeNewDomainFlags_NoSecurityChanges`|Ortak dil çalışma zamanına (CLR), ana bilgisayarın yöntemdeki uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı konusunda bilgilendirir <xref:System.AppDomainManager.InitializeNewDomain%2A> .|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alır `EInitializeNewDomainFlags` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
- [SetAppDomainManagerType Yöntemi](iclrdomainmanager-setappdomainmanagertype-method.md)
