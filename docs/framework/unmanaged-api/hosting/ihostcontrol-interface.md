---
description: 'Daha fazla bilgi edinin: IHostControl arabirimi'
title: IHostControl Arabirimi
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: e7a242ed0fdaa734425bec9b48f01fe45cba5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789469"
---
# <a name="ihostcontrol-interface"></a>IHostControl Arabirimi

Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetHostManager Yöntemi](ihostcontrol-gethostmanager-method.md)|Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .|  
|[SetAppDomainManager Yöntemi](ihostcontrol-setappdomainmanager-method.md)|Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
