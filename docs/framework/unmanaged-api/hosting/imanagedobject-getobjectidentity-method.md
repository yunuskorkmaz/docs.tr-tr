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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141251"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity Metodu
Bu yönetilen nesnenin kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBSTRGUID`  
 dışı Nesnenin bulunduğu işlemin GUID 'sine yönelik bir işaretçi.  
  
 `AppDomainID`  
 dışı Nesnenin uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.  
  
 `pCCW`  
 dışı COM klasik v tablosundaki nesnenin dizinine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen bir nesnenin kimliği işlem GUID 'SI, uygulama etki alanı KIMLIĞI ve nesnenin dizinini, COM klasik v-tablosunda içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IManagedObject Arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
