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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126621"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager Arabirimi
Derlemeler hakkında, ana bilgisayar ve ortak dil çalışma zamanı (CLR) arasındaki iletişimi destekleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBindingIdentityFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.|  
|[GetBindingIdentityFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.|  
|[GetCLRAssemblyReferenceList Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) örneği alır.|  
|[GetProbingAssembliesFromReference Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Belirtilen kimliğe sahip derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.|  
|[GetReferencedAssembliesFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) örneğini alır.|  
|[GetReferencedAssembliesFromStream Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren `ICLRReferenceAssemblyEnum` nesnesine yönelik bir işaretçi alır.|  
|[IsStronglyNamed Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRAssemblyReferenceList` örneklerini almak ve derleme kimliklerini numaralandırmak için `ICLRAssemblyIdentityManager` kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
