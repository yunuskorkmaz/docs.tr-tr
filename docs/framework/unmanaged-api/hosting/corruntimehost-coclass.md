---
title: "CorRuntimeHost Coclass’ı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Coclass’ı
Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirim sağlar.  
  
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
|[ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemleri sağlar.|  
|[ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Ortak dil çalışma zamanı oluşturmak ve uygulama etki alanları, varsayılan etki alanı erişmek ve tüm etki alanları işlemde çalışan listeleme için yapılandırmak için açıkça durdurmak ve başlatmak ana bilgisayar sağlayan yöntemler sağlar.|  
|[IDebuggerInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemleri sağlar.|  
|[IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.|  
|"IValidator"|Taşınabilir yürütülebilir görüntüler doğrulanması ve ayrıntılı doğrulama hatalarını raporlama için yöntemleri sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Coclassları](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
