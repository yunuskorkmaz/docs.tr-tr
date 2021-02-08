---
description: ': ICLRDomainManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d719e89d81e8c7abb1f238ce50b4e236de17ac72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790015"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager Arabirimi

Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetAppDomainManagerType Yöntemi](iclrdomainmanager-setappdomainmanagertype-method.md)|<xref:System.AppDomainManager?displayProperty=nameWithType>Varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.|  
|[SetPropertiesForDefaultAppDomain Yöntemi](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirimin bir örneğini almak için, yönetici türü IID ile [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırın `IID_ICLRDomainManager` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
