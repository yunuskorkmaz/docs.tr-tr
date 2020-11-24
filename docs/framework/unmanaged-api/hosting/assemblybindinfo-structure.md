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
ms.openlocfilehash: d2ba7d8e66472f771a932a2dfb05bb9e1ee96290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685883"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo Yapısı

Başvurulan derleme hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)
- [ModuleBindInfo Yapısı](modulebindinfo-structure.md)
