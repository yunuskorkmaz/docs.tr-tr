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
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805049"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager Arabirimi
Bir konağın ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAssemblyStore Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.|  
|[GetNonHostStoreAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|Konağın CLR 'nin yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak veya uygulamak için gerekli değildir `IHostAssemblyManager` `IHostAssemblyStore` . Ana bilgisayar uygulıyorsa `IHostAssemblyManager` , de uygulaması gerekir `IHostAssemblyStore` .  
  
 Çalışma zamanı, bir `IHostAssemblyManager` IID_IHostAssemblyManager ile başlatma sonrasında [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) çağırarak bir için sorgular `IID` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)
- [IHostControl Arabirimi](ihostcontrol-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
