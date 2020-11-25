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
ms.openlocfilehash: 7c77cb2e89cb8fd87bf219780b9460649de19c9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731777"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost Coclass’ı

Çalışma zamanı tarafından kod yürütmeyi yönetmek için arabirimler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>Arabirimler  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|[ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)|Çalışma zamanı tarafından uygulamaların yürütülmesini denetlemek için yöntemler sağlar.|  
|[ICLRValidator Arabirimi](iclrvalidator-interface.md)|Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yardımcı Sınıfları](hosting-coclasses.md)
