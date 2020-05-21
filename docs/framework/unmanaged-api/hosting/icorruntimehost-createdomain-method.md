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
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762363"
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain Yöntemi
Bir uygulama etki alanı oluşturur. Çağıran, türünde bir örneğine türünde bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFriendlyName`  
 'ndaki Etki alanına kolay bir ad vermek için kullanılan isteğe bağlı bir parametre. Bu kolay ad, etki alanını tanımlamak için hata ayıklayıcılar gibi kullanıcı arabirimlerinde gösterilebilir.  
  
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
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
