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
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762350"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx Yöntemi
Bir uygulama etki alanı oluşturur. Çağıran, türünde bir tür örneğine bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> . Bu yöntem, çağıranın döndürülen örneğin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar <xref:System._AppDomain> .  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `IAppDomainSetup` [ICorRuntimeHost:: CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) yöntemine yapılan bir çağrı ile elde edilen isteğe bağlı bir arabirim türü.  
  
 `pIdentityArray`  
 'ndaki `IIdentity`Bir izin kümesi oluşturmak için güvenlik ilkesiyle eşlenen kanıtları temsil eden örneklere yönelik işaretçilerin bir dizisi. Bir `IIdentity` nesnesi [createkanıt](icorruntimehost-createevidence-method.md) yöntemi çağırarak elde edilebilir.  
  
 `pAppDomain`  
 dışı <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> Etki alanını daha fazla denetlemek için kullanılan bir örneğine türünde bir arabirim işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAIL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateDomainEx`çağıranın, uygulama etki alanını yapılandırmak için özellik değerleriyle bir örnek geçmesine izin vererek [CreateDomain](icorruntimehost-createdomain-method.md) 'in yeteneklerini genişletir `IAppDomainSetup` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain Yöntemi](icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
