---
title: "ICorRuntimeHost::CreateDomainEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 042befa2dd96ad9f6e6dd3069ba2c4aabcd146fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx Yöntemi
Uygulama etki alanı oluşturur. Arayan türünde bir arabirim işaretçisi alır <xref:System._AppDomain>, türünün bir örneği için <xref:System.AppDomain?displayProperty=nameWithType>. Bu yöntem döndürülen ek özelliklerini yapılandırmak için Iappdomainsetup örneği geçirmek arayan sağlar <xref:System._AppDomain> örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzFriendlyName`  
 [in] Etki alanı için kolay bir ad vermek için kullanılan isteğe bağlı bir parametre. Bu kolay adı etki alanını tanımlamak için hata ayıklayıcıları gibi kullanıcı arabirimleri görüntülenebilir.  
  
 `pSetup`  
 [in] Bir isteğe bağlı bir arabirim işaretçisi türü `IAppDomainSetup`, bir çağrı tarafından alınan [Icorruntimehost::createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) yöntemi.  
  
 `pIdentityArray`  
 [in] İşaretçiler isteğe bağlı bir dizi `IIdentity` bir izin kümesi oluşturmak için Güvenlik İlkesi aracılığıyla eşlenen kanıt temsil örnekleri. Bir `IIdentity` nesne elde edilebilir çağırarak [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi.  
  
 `pAppDomain`  
 [out] Arabirim işaretçisi türü <xref:System._AppDomain> örneğine <xref:System.AppDomain?displayProperty=nameWithType> daha fazla etki alanı denetlemek için kullanılabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlemi tamamlayamadı.|  
|E_FAIL|Bilinmeyen, geri dönülemez bir hata oluştu. Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz. Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateDomainEx`yeteneklerini genişletir [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) arayan geçirin sağlayarak bir `IAppDomainSetup` uygulama etki alanını yapılandırmak için özellik değerlerini örneğiyle.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümü:** 1.0, 1.1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [CreateDomain yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [Icorruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
