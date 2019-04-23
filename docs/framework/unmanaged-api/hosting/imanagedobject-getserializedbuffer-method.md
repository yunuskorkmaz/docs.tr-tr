---
title: IManagedObject::GetSerializedBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb9242160b684b3c7b90756d7b20811ad162fc30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156149"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>IManagedObject::GetSerializedBuffer Yöntemi
Bu yönetilen bir nesnenin dize gösterimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBSTR`  
 [out] Serileştirilmiş nesne bir dizeye bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IManagedObject Arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
