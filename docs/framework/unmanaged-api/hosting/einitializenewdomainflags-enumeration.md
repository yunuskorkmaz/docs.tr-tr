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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431455"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags Numaralandırması
Çalışma zamanı uygulama etki alanı başlatma hakkında bilgi sağlamak ana bilgisayarı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Hiçbir bayraklar.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Ortak dil çalışma zamanı (CLR) ana uygulama etki alanı güvenlik durumunu bir değişiklik değil olduğunu bildiren <xref:System.AppDomainManager.InitializeNewDomain%2A> yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrdomainmanager::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alan `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [SetAppDomainManagerType Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
