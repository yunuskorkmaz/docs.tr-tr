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
ms.openlocfilehash: 505015877985492edab4b761b379f33f1e5c6660
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729986"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo Yapısı

Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
|`dwAppDomainId`|`IStream`Başvurulan modülün yükleneceği [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) yöntemine yapılan bir çağrı tarafından döndürülen benzersiz bir tanımlayıcı.|  
|`lpAssemblyIdentity`|Başvurulan modülü içeren derleme için benzersiz bir tanımlayıcı.|  
|`lpModuleName`|Başvurulan modülün adı.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ModuleBindInfo` parametresi olarak geçirilir `IHostAssemblyStore::ProvideModule` . Ana bilgisayar, `dwAppDomainId` ortak dil çalışma zamanına (CLR) benzersiz tanımlayıcıyı sağlar. [IHostAssemblyStore ' a bir çağrıdan sonra::P rovideAssembly](ihostassemblystore-provideassembly-method.md) yöntemi döndürülürse, çalışma zamanı, ' ın içeriklerinin `IStream` eşlenip eşlenmediğini anlamak için tanımlayıcıyı kullanır. Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler. Çalışma zamanı Ayrıca bu tanımlayıcıyı, metoduna yapılan çağrılardan döndürülen akışlar için bir arama anahtarı olarak kullanır `IHostAssemblyStore::ProvideAssembly` . Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [AssemblyBindInfo Yapısı](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
