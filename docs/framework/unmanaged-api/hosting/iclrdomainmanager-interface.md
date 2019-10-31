---
title: ICLRDomainManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129336"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager Arabirimi
Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetAppDomainManagerType Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|Varsayılan uygulama etki alanını başlatmak için kullanılacak olan uygulama etki alanı yöneticisinin <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfından türetilen türü belirtir.|  
|[SetPropertiesForDefaultAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirimin bir örneğini almak için, yönetici türü IID `IID_ICLRDomainManager`[ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
