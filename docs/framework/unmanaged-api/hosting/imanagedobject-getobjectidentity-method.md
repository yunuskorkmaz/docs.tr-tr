---
title: IManagedObject::GetObjectIdentity Metodu
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d825a0c67f88e1f37023feb96a217b115653056
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496943"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity Metodu
Bu yönetilen nesne kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBSTRGUID`  
 [out] Nesnenin bulunduğu işlem GUİD'si işaretçisi.  
  
 `AppDomainID`  
 [out] Nesnenin uygulama etki alanı kimliği için bir işaretçi.  
  
 `pCCW`  
 [out] Nesnenin dizinde COM Klasik v tablo için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen bir nesnenin kimliğini COM Klasik v tablosunda işlem GUID'si, uygulama etki alanı kimliği ve nesnenin dizin içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IManagedObject Arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
