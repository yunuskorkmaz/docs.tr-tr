---
title: ICorRuntimeHost::GetDefaultDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139560"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a>ICorRuntimeHost::GetDefaultDomain Yöntemi
Geçerli işlem için varsayılan etki alanını temsil eden <xref:System._AppDomain?displayProperty=nameWithType> türünde bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 dışı İşlem için varsayılan uygulama etki alanını temsil eden <xref:System.AppDomain> örneğine <xref:System._AppDomain?displayProperty=nameWithType> türünde bir arabirim işaretçisi.  
  
 Bu işaretçi `IUnknown`yazılır, bu nedenle çağıranlar genellikle <xref:System._AppDomain?displayProperty=nameWithType>türünde bir arabirim işaretçisi almak için `QueryInterface` çağırmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAıL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
