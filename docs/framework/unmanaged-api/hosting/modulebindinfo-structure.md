---
title: "ModuleBindInfo Yapısı"
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
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo Yapısı
Başvurulan modül ve içerdiği derleme hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwAppDomainId`|İçin benzersiz bir tanımlayıcı `IStream` için yapılan bir çağrı tarafından döndürülen [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) başvurulan modül olduğu yüklenecek yöntemi.|  
|`lpAssemblyIdentity`|Başvurulan modül içeren derlemenin için benzersiz bir tanımlayıcı.|  
|`lpModuleName`|Başvurulan modül adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ModuleBindInfo`bir parametre olarak geçirilen `IHostAssemblyStore::ProvideModule`. Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR) için. Çağrı sonra [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) yöntemi döndürür, çalışma zamanı belirlemek için tanımlayıcısını kullanır olup olmadığını içeriğini `IStream` eşlenmedi. Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler. Çalışma zamanı bu tanımlayıcı ayrıca çağrılardan döndürülen akışlar için arama anahtar olarak kullanır `IHostAssemblyStore::ProvideAssembly` yöntemi. Bu nedenle, tanımlayıcı derleme istekleri için de modülü istekleri için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [AssemblyBindInfo Yapısı](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
