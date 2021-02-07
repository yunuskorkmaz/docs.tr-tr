---
description: "Daha fazla bilgi edinin: CorRuntimeHost coclass 'ı"
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
ms.openlocfilehash: cd2d01075e5c8264337e1e989b3d9fdc6bf68962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760648"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Ortak Sınıfı

Ortak dil çalışma zamanı tarafından yürütülen uygulamaları yönetmek için arabirimler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Arabirim|Description|  
|---------------|-----------------|  
|[ICorConfiguration Arabirimi](icorconfiguration-interface.md)|Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.|  
|[ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)|Ana bilgisayarın ortak dil çalışma zamanını başlatma ve durdurma, varsayılan etki alanına erişme ve işlemde çalışan tüm etki alanlarını listeleme gibi yöntemleri sağlar.|  
|[IDebuggerInfo Arabirimi](idebuggerinfo-interface.md)|Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.|  
|[IGCHost Arabirimi](igchost-interface.md)|Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.|  
|IValidator|Taşınabilir yürütülebilir görüntülerin doğrulanması ve doğrulama hatalarının ayrıntılı raporlanması için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yardımcı Sınıfları](hosting-coclasses.md)
