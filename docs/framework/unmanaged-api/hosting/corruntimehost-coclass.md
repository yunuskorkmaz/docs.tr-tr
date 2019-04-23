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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218569"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Ortak Sınıfı
Ortak dil çalışma zamanı tarafından yürütülen uygulamalarını yönetmek için arabirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|[ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemler sağlar.|  
|[ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Ortak dil çalışma zamanı oluşturma ve uygulama etki alanları, varsayılan etki alanına ve işlemde çalışan tüm etki alanları listelemek için yapılandırma açıkça durdurmak ve başlatmak konak olanak tanıyan yöntemler sağlar.|  
|[IDebuggerInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Hata Ayıklama Hizmetleri durumuyla ilgili bilgileri almak için yöntemler sağlar.|  
|[IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.|  
|"IValidator"|Taşınabilir yürütülebilir görüntü doğrulama ve ayrıntılı doğrulama hatalarını raporlama için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Coclassları](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
