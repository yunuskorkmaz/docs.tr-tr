---
description: ': ICorRuntimeHost:: UnloadDomain metodu hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::UnloadDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: b191f2342778b2f2ed7ddb7b1fb548c73be96599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799403"
---
# <a name="icorruntimehostunloaddomain-method"></a>ICorRuntimeHost::UnloadDomain Yöntemi

Belirtilen uygulama etki alanını geçerli işlemden kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAppDomain`  
 'ndaki <xref:System._AppDomain?displayProperty=nameWithType> Kaldırılacak etki alanını temsil eden tür işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAIL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
