---
title: ICLRHostProtectionManager::SetProtectedCategories Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e34c14ce9f063653c9d0018733f93e398641355
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569855"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories Yöntemi
Yönetilen türler ve üyeler kategorilerini kısmen güvenilen bir kod çalıştırmasını engellenmesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `categories`  
 [in] Bir birleşimi [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) Kategorilerini Yönetilen türlerin ve üyelerin kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini belirten değerleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her `EApiCategories` değeri Yönetilen türlerin ve üyelerin listesini gösterir. `EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili için yönetilen <xref:System.Security.Permissions.HostProtectionAttribute> yönetilen türleri ve üyeleri tarafından açıklanan kategoriler karşılık gelen özellikleri kullanıma sunan işaretlemek için kullanılan sınıfı `EApiCategories`. Daha fazla bilgi için <xref:System.Security.Permissions.HostProtectionAttribute> ve <xref:System.Security.Permissions.HostProtectionResource> doğrudan karşılık gelen numaralandırma `EApiCategories`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [EApiCategories Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
