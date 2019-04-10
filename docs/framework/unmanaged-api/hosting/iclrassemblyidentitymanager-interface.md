---
title: ICLRAssemblyIdentityManager Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209807"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager Arabirimi
Derlemeler hakkında ortak dil çalışma zamanı (CLR) ile konak arasındaki iletişimi desteklemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBindingIdentityFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Belirtilen dosya yolunda derleme için veri bağlama derleme kimliğini alır.|  
|[GetBindingIdentityFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.|  
|[GetCLRAssemblyReferenceList Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.|  
|[GetProbingAssembliesFromReference Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirtilen kimliğine sahip derleme tarafından başvurulan derleme kimlikleri için Numaralandırıcı.|  
|[GetReferencedAssembliesFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolunda derlemesi tarafından başvurulan derlemelerin bir listesini içeren örneği.|  
|[GetReferencedAssembliesFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Bir işaretçi alır bir `ICLRReferenceAssemblyEnum` belirtilen akış derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.|  
|[IsStronglyNamed Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Belirtilen derleme kesin şekilde adlandırıldığında olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `ICLRAssemblyIdentityManager` örneklerini almak için `ICLRAssemblyReferenceList` ve derleme kimlikleri numaralandırılamadı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
