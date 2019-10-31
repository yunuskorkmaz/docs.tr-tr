---
title: ICorRuntimeHost::CreateDomainEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: a3a2d1827774ddedc00eb849f64256e3f425b3fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127719"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx Yöntemi
Bir uygulama etki alanı oluşturur. Çağıran, <xref:System.AppDomain?displayProperty=nameWithType>türünde bir örneğe <xref:System._AppDomain>türünde bir arabirim işaretçisi alır. Bu yöntem, çağıranın döndürülen <xref:System._AppDomain> örneğinin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFriendlyName`  
 'ndaki Etki alanına kolay bir ad vermek için kullanılan isteğe bağlı bir parametre. Bu kolay ad, etki alanını tanımlamak için hata ayıklayıcılar gibi kullanıcı arabirimlerinde gösterilebilir.  
  
 `pSetup`  
 'ndaki [ICorRuntimeHost:: CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) yöntemine yapılan bir çağrı ile elde edilen `IAppDomainSetup`türünde isteğe bağlı bir arabirim işaretçisi.  
  
 `pIdentityArray`  
 'ndaki Bir izin kümesi oluşturmak için güvenlik ilkesiyle eşlenen kanıtları temsil eden `IIdentity` örneklerine yönelik bir işaretçi dizisi. `IIdentity` nesnesi [Createkanıt](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi çağırarak elde edilebilir.  
  
 `pAppDomain`  
 dışı Etki alanını daha fazla denetlemek için kullanılabilecek bir <xref:System.AppDomain?displayProperty=nameWithType> örneğine <xref:System._AppDomain> türünde bir arabirim işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAıL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateDomainEx`, çağıranın uygulama etki alanını yapılandırmak için özellik değerleriyle `IAppDomainSetup` bir örnek geçmesine izin vererek [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) 'ın yeteneklerini genişletir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
