---
title: ICorRuntimeHost::CreateEvidence Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 264f16fc9e767584229376e67f5aee6db1069025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501618"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence Yöntemi
<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, Konağın [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna geçirilecek güvenlik kanıtı oluşturmasına izin veren, türünde bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pEvidence`  
 dışı <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>Güvenlik kanıtı oluşturmak için kullanılan bir örneğe yönelik arabirim işaretçisi. Bu işaretçi yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` bir işaretçi almak için tipik olarak bu arabirimi çağırmalıdır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAIL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yerel koddan doldurulamadı boş bir koleksiyon döndürür. <xref:System.Security.Policy.Evidence>Bunun yerine yöntemini kullanmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
