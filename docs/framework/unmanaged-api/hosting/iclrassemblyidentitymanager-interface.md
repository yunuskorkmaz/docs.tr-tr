---
title: ICLRAssemblyIdentityManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager Arabirimi
Derlemeler hakkında ortak dil çalışma zamanı (CLR) ile konak arasındaki iletişimi destekleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBindingIdentityFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Belirtilen dosya yolu konumunda derlemesi için veri bağlama derleme kimliğini alır.|  
|[GetBindingIdentityFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.|  
|[GetCLRAssemblyReferenceList Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.|  
|[GetProbingAssembliesFromReference Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirtilen kimliğe sahip derlemesi tarafından başvurulan derleme kimlikleri için Numaralandırıcı.|  
|[GetReferencedAssembliesFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolu konumunda derlemesi tarafından başvurulan bir derleme listesi içeren örneği.|  
|[GetReferencedAssembliesFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Bir işaretçi alır bir `ICLRReferenceAssemblyEnum` belirtilen stream derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.|  
|[IsStronglyNamed Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Belirtilen derleme güçlü olarak adlandırılmamış olup olmadığını belirten bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `ICLRAssemblyIdentityManager` örneklerini almak için `ICLRAssemblyReferenceList` ve derleme kimlikleri numaralandırılamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [ICLRProbingAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
