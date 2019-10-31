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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131210"
---
# <a name="eapicategories-enumeration"></a>EApiCategories Numaralandırması
Ana bilgisayarın kısmen güvenilen kodda çalışmasını engelleyebilecekleri yetenekler kategorilerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`eAll`|Diğer `EApiCategories` alanları kapsamındaki tüm yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.|  
|`eExternalProcessMgmt`|Dış işlemlerin oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.|  
|`eExternalThreading`|Dış iş parçacıklarının oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.|  
|`eMayLeakOnAbort`|Durdurma sırasında belleği potansiyel olarak sızan yönetilen türlerin ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenebileceği belirtir.|  
|`eNoCategory`|Kısmen güvenilen kodda çalıştırmanın hiçbir yönetilen kod kategorisinin engellenip engellenmediğini belirtir.|  
|`eSecurityInfrastructure`|Ortak dil çalışma zamanı (CLR) güvenlik altyapısının kısmen güvenilen kod tarafından kullanılmasını engellenemediğini belirtir.|  
|`eSelfAffectingProcessMgmt`|Özellikleri barındırılan işlemi etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.|  
|`eSelfAffectingThreading`|Özellikleri barındırılan işlemdeki iş parçacıklarını etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.|  
|`eSharedState`|Paylaşılan durum sergilemiş olan yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.|  
|`eSynchronization`|Ortak dil çalışma zamanı sınıflarının ve kullanıcı kodunun kilitleri tutmaya izin veren üyelerin kısmen güvenilen kodda çalıştırılmasını engellediği belirtir.|  
|`eUI`|İnsan etkileşiminin kısmen güvenilen kodda çalışmasına izin veren veya bunları gerektiren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRHostProtectionManager:: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi, `EApiCategories`türünde bir parametre alır.  
  
 `EApiCategories` numaralandırması ve `SetProtectedCategories` yöntemi, yönetilen <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfıyla doğrudan ilgilidir. Yönetilen sınıf, `EApiCategories`tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için değerleri doğrudan `EApiCategories` değerlerine karşılık gelen <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırmasında kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
