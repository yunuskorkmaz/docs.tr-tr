---
title: IHostAssemblyManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118956"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager Arabirimi
Ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derlemeler kümesini belirtmek konak izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAssemblyStore Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derlemelerin listesini temsil eder.|  
|[GetNonHostStoreAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) yüklenecek CLR konak bekliyor derlemelerin listesini temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak uygulamak için gerekli olmayan `IHostAssemblyManager` veya `IHostAssemblyStore`. Konak uygularsanız `IHostAssemblyManager`, ayrıca uygulamalıdır `IHostAssemblyStore`.  
  
 Çalışma zamanı sorgular için bir `IHostAssemblyManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) ile başlatma sırasında bir `IID` IID_IHostAssemblyManager biri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
