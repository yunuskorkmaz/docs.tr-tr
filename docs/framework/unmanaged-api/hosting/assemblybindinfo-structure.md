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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112820"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo Yapısı
Başvurulan derleme hakkında ayrıntılı bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`dwAppDomainId`|İçin benzersiz bir tanımlayıcı `IStream` bir çağrı tarafından döndürülen [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), başvurulan derleme yüklenecek olan öğesinden.|  
|`lpReferencedIdentity`|Başvurulan derleme için benzersiz bir tanımlayıcı.|  
|`lpPostPolicyIdentity`|Başvurulan derleme bağlama ilkesi değerleri uygulandıktan sonra tanımlayıcısı.|  
|`ePolicyLevel`|Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hangi sürüm ilkeleri varsa, başvurulan derlemeye uygulanması gerektiğini gösteren değerleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR). Çağrısı yapıldıktan sonra `IHostAssemblyStore::ProvideAssembly` döndürür, çalışma belirlemek için tanımlayıcı kullandığı olmadığını içeriğini `IStream` eşlendi. Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler. Döndürülen akışlar için çalışma zamanı bu tanımlayıcıyı ayrıca arama anahtar olarak kullanır. çağrılar [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Bu nedenle, tanımlayıcı derleme isteklerini ve modülün istekleri için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo Yapısı](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
