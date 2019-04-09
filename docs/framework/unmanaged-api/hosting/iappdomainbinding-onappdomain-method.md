---
title: IAppDomainBinding::OnAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2903395f5f834f2435b14d0b3f3e8bfe24af2867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183059"
---
# <a name="iappdomainbindingonappdomain-method"></a>IAppDomainBinding::OnAppDomain Yöntemi
Ortak dil çalışma zamanı tarafından ana bilgisayara bir uygulama etki alanı oluşturulduğunu bildirmek için (CLR) çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppdomain`  
 [in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) yeni uygulama etki alanını temsil eden arabirim nesne.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAppDomainBinding Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
