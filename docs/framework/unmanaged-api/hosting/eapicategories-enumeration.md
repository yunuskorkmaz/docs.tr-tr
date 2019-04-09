---
title: EApiCategories Numaralandırması
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086461"
---
# <a name="eapicategories-enumeration"></a>EApiCategories Numaralandırması
Konak, kısmen güvenilen bir kod çalıştırmasını engelleyebilir özellikleri kategorileri açıklanmaktadır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eAll`|Tüm yönetilen sınıflar ve diğer tarafından kapsanan üyeleri belirtir `EApiCategories` alanlar, kısmen güvenilen bir kod çalıştırmasını engellenir.|  
|`eExternalProcessMgmt`|Yönetilen sınıflar ve oluşturma, düzenleme ve yok edilmesini dış işlemlere izin üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eExternalThreading`|Yönetilen sınıflar ve oluşturma, düzenleme ve dış iş parçacıklarını yok edilmesini sağlayan üyeleri kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eMayLeakOnAbort`|Yönetilen türler ve potansiyel olarak iptal bellek dışarıya sızmasına neden olabilecek bir üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eNoCategory`|Yönetilen kod kategori kısmen güvenilen kod çalıştırılmasının engellenmesi belirtir.|  
|`eSecurityInfrastructure`|Ortak dil çalışma zamanı (CLR) güvenlik altyapısı kısmen güvenilen kod tarafından kullanılan engelleneceğini belirtir.|  
|`eSelfAffectingProcessMgmt`|Yönetilen sınıflar ve üyeleri olan yetenekleri barındırılan işlem etkileyebilir kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eSelfAffectingThreading`|Yönetilen sınıflar ve üyeleri olan yetenekleri barındırılan işlemdeki iş parçacıkları etkileyebilir kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eSharedState`|Yönetilen sınıflar ve paylaşılan durum kullanıma üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eSynchronization`|Ortak dil çalışma zamanı sınıflar ve kullanıcı kodu için kilitler barındırmıyorsa izin üyeleri kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
|`eUI`|Yönetilen sınıflar ve izin veren veya insan etkileşimi gerektiren üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi türünde bir parametre alır `EApiCategories`.  
  
 `EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili için yönetilen <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfı. Yönetilen sınıf ile kullanılan <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırma değerleri karşılık doğrudan `EApiCategories` yönetilen türleri ve üyeleri tarafından açıklanan kategoriler karşılık gelen özellikleri kullanıma sunan işaretlemek için değerleri `EApiCategories`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Barındırma Numaralandırmaları](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
