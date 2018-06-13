---
title: IManagedObject::GetSerializedBuffer Metodu
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
ms.openlocfilehash: 53e8180fb55336eb05d0737110fd2fe07a4c5894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441607"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>IManagedObject::GetSerializedBuffer Metodu
Bu yönetilen nesne dize gösterimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBSTR`  
 [out] Serileştirilmiş nesne olan bir dize için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IManagedObject Arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
