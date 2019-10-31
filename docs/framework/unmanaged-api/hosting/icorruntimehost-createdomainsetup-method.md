---
title: ICorRuntimeHost::CreateDomainSetup Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139654"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a>ICorRuntimeHost::CreateDomainSetup Yöntemi
Bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneğine IAppDomainSetup türünde bir arabirim işaretçisi alır. `IAppDomainSetup`, bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomainSetup`  
 dışı <xref:System.AppDomainSetup?displayProperty=nameWithType> örneğine yönelik arabirim işaretçisi. Bu parametre `IUnknown`olarak yazılır, bu nedenle çağıranlar genellikle `IAppDomainSetup`türünde bir arabirim işaretçisi almak için bu işaretçi üzerinde `QueryInterface` çağırmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAıL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemden döndürülen işaretçi genellikle [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoduna parametre olarak geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
