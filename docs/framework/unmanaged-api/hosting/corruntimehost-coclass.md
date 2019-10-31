---
title: CorRuntimeHost Ortak Sınıfı
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136903"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Ortak Sınıfı
Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Arabirimler  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|[ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.|  
|[ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.|  
|[IDebuggerInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.|  
|[IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.|  
|IValidator|Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Coclassları](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
