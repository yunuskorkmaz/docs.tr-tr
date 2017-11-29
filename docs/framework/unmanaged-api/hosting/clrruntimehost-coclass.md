---
title: "CLRRuntimeHost Coclass’ı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost Coclass’ı
Kod yürütmeyi çalışma zamanı tarafından yönetmek için arabirim sağlar.  
  
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
|[Iclrruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|Çalışma zamanı tarafından uygulamaların yürütülmesini denetleme yöntemleri sağlar.|  
|[Iclrvalidator arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma coclass'ları](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
