---
title: "EApiCategories Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 630a3048072ed7b19b3250e75aca3b31e4dd7df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="eapicategories-enumeration"></a>EApiCategories Numaralandırması
Ana bilgisayar kısmen güvenilen bir kod çalıştırmasını engelleyebilir yeteneklerini kategorileri açıklanmaktadır.  
  
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
|`eAll`|Tüm sınıflar ve üyeleri tarafından kapsanan yönetilen belirtir `EApiCategories` alanları, kısmen güvenilen kodu çalıştırma engellenir.|  
|`eExternalProcessMgmt`|Yönetilen sınıflar ve oluşturma, düzenleme ve dış işlemlere edilmesine izin üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eExternalThreading`|Yönetilen sınıflar ve oluşturma, düzenleme ve dış iş parçacıklarını yok etme izin üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eMayLeakOnAbort`|Yönetilen türler ve iptal bellek sızıntısı üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eNoCategory`|Yönetilen kod kategori yok kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eSecurityInfrastructure`|Ortak dil çalışma zamanı (CLR) güvenlik altyapısı kısmen güvenilen kod tarafından kullanılan engelleneceğini belirtir.|  
|`eSelfAffectingProcessMgmt`|Yönetilen sınıflar ve üyeleri olan özellikleri barındırılan işlem etkileyebilir kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eSelfAffectingThreading`|Yönetilen sınıflar ve üyeleri olan özellikleri barındırılan işlemdeki iş parçacıklarının etkileyebilir kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eSharedState`|Yönetilen sınıflar ve paylaşılan durum kullanıma üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eSynchronization`|Ortak dil çalışma zamanı sınıflar ve kilitleri tutmak kullanıcı kodu izin üyeleri kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
|`eUI`|Yönetilen sınıflar ve izin veren veya insan etkileşimi gerektiren üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi türünde bir parametre alan `EApiCategories`.  
  
 `EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili yönetilen için <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfı. Yönetilen sınıf ile kullanılan <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırma, karşılık gelen değerleri doğrudan `EApiCategories` işareti yönetilen türler ve özellikleri tarafından açıklanan kategoriye karşılık gelen açığa üyeleri değerleri, `EApiCategories`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
