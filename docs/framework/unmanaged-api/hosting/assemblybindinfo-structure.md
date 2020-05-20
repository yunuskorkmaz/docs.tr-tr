---
title: AssemblyBindInfo Yapısı
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616935"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo Yapısı
Başvurulan derleme hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwAppDomainId`|`IStream` [IHostAssemblyStore](ihostassemblystore-provideassembly-method.md)çağrısı tarafından döndürülen benzersiz bir tanımlayıcı::P rovideassembly, başvurulan derlemenin yükleneceği.|  
|`lpReferencedIdentity`|Başvurulan derleme için benzersiz bir tanımlayıcı.|  
|`lpPostPolicyIdentity`|Bağlama ilkesi değerlerinin uygulamadan sonra başvurulan derlemenin tanımlayıcısı.|  
|`ePolicyLevel`|Varsa, başvurulan derlemeye hangi sürüm oluşturma ilkelerinin uygulanacağını belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar, `dwAppDomainId` ortak dil çalışma zamanına (CLR) benzersiz tanımlayıcıyı sağlar. Bir çağrıdan sonra `IHostAssemblyStore::ProvideAssembly` , çalışma zamanı, ' ın içeriklerinin eşlenip eşlenmediğini anlamak için tanımlayıcıyı kullanır `IStream` . Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler. Çalışma zamanı Ayrıca bu tanımlayıcıyı [IHostAssemblyStore](ihostassemblystore-providemodule-method.md)çağrılarından döndürülen akışlar için bir arama anahtarı olarak kullanır::P rovideModule. Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)
- [ModuleBindInfo Yapısı](modulebindinfo-structure.md)
