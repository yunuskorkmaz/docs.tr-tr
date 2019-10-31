---
title: ModuleBindInfo Yapısı
ms.date: 03/30/2017
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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133741"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo Yapısı
Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwAppDomainId`|Başvurulan modülün yükleneceği [IHostAssemblyStore::P rovideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) yöntemine yapılan bir çağrı tarafından döndürülen `IStream` için benzersiz bir tanımlayıcı.|  
|`lpAssemblyIdentity`|Başvurulan modülü içeren derleme için benzersiz bir tanımlayıcı.|  
|`lpModuleName`|Başvurulan modülün adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ModuleBindInfo`, `IHostAssemblyStore::ProvideModule`bir parametre olarak geçirilir. Ana bilgisayar, ortak dil çalışma zamanına (CLR) `dwAppDomainId` benzersiz tanımlayıcıyı sağlar. [IHostAssemblyStore ' a bir çağrıdan sonra::P rovideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) yöntemi dönerse, çalışma zamanı `IStream` içeriğinin eşlenip eşleştirilmediğini anlamak için tanımlayıcıyı kullanır. Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler. Çalışma zamanı Ayrıca bu tanımlayıcıyı, `IHostAssemblyStore::ProvideAssembly` metoduna yapılan çağrılardan döndürülen akışlar için bir arama anahtarı olarak kullanır. Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo Yapısı](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
