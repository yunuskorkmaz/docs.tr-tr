---
title: CLRRuntimeHost Coclass’ı
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e40f08a3dae6f17617e97e07a23b9d7eb611083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558637"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost Coclass’ı
Kod yürütme çalışma zamanı tarafından yönetmek için arabirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>Arabirimler  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|[ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.|  
|[ICLRValidator Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|Doğrulama hatalarını ayrıntılı raporlama için ve doğrulama taşınabilir yürütülebilir görüntü için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Coclassları](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
