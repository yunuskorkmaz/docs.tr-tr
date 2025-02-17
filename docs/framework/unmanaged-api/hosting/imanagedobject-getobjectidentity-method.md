---
description: 'Şu konuda daha fazla bilgi edinin: IManagedObject:: GetObjectIdentity yöntemi'
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
ms.openlocfilehash: 8929819bbf490680b5f3f1f47b9f3b8e830d57ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671171"
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

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IManagedObject Arabirimi](imanagedobject-interface.md)
