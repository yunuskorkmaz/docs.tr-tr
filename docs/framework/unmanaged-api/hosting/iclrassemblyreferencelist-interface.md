---
title: ICLRAssemblyReferenceList Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43c40e833e3a250239e9e90667196a2a74a96e0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187661"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList Arabirimi
Ortak dil çalışma zamanı (CLR) ve ana bilgisayar tarafından yüklenen derlemelerin bir listesini yönetir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IsAssemblyReferenceInList Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Sağlanan işaretçi listedeki bir derleme başvuruda bulunup bulunmadığını belirten bir değer alır.|  
|[IsStringAssemblyReferenceInList Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Sağlanan ad listesinde bir derlemenin adı ile eşleşip eşleşmediğini gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı [Iclrassemblyıdentitymanager::getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) örneğine bir işaretçi almak için yöntemi `ICLRAssemblyReferenceList`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
