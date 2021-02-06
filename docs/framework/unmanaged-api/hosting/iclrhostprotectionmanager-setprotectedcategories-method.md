---
description: ': ICLRHostProtectionManager:: SetProtectedCategories yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9138c31ea1a2d9b7ebeaeac8ef5ef9305eabef8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637540"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories Yöntemi

Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını engelleneceğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `categories`  
 'ndaki Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını önlenebileceğini belirten [EApiCategories](eapicategories-enumeration.md) değerlerinin bir birleşimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Her `EApiCategories` değer, yönetilen türlerin ve üyelerin listesini ifade eder. `EApiCategories`Sabit listesi ve `SetProtectedCategories` yöntemi, <xref:System.Security.Permissions.HostProtectionAttribute> tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için kullanılan yönetilen sınıfla doğrudan ilgilidir `EApiCategories` . Daha fazla bilgi için, bkz <xref:System.Security.Permissions.HostProtectionAttribute> <xref:System.Security.Permissions.HostProtectionResource> . ve doğrudan karşılık gelen sabit listesi `EApiCategories` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [EApiCategories Numaralandırması](eapicategories-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRHostProtectionManager Arabirimi](iclrhostprotectionmanager-interface.md)
