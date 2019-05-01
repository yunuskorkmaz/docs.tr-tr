---
title: ICorRuntimeHost::CreateDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea63627bc1e689c93634c8fe8b9048b271758573
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937058"
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain Yöntemi
Uygulama etki alanı oluşturur. Çağıranın türü bir arabirim işaretçisi alır <xref:System._AppDomain> türde bir örnek <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFriendlyName`  
 [in] Etki alanında kolay bir ad vermek için kullanılan isteğe bağlı bir parametre. Bu kolay adı, etki alanını tanımlamak için hata ayıklayıcıları gibi kullanıcı arabirimlerinde görüntülenebilir.  
  
 `pIdentityArray`  
 [in] İsteğe bağlı bir işaretçiler dizisi `IIdentity` kanıt eşlenmiş bir izin kümesi oluşturmak için Güvenlik İlkesi aracılığıyla temsil eden örnekleri. Bir `IIdentity` nesnesi elde edilebilir çağırarak [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi.  
  
 `pAppDomain`  
 [out] Bir arabirim işaretçisi türünde <xref:System._AppDomain> örneğine <xref:System.AppDomain?displayProperty=nameWithType> daha fazla etki alanı kontrol etmek için kullanılabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlemi tamamlayamadı.|  
|E_FAIL|Bilinmeyen, geri dönülemez bir hata oluştu. Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz. Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** 1.0, 1.1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
