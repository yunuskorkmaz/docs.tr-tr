---
title: ICLRRuntimeHost Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
Benzer işlevsellik sağlar [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework sürüm 1, aşağıdaki değişiklikleri ile sağlanan arabirim:  
  
-   Eklenmesi [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) ana denetim arabirimi ayarlamak için yöntem.  
  
-   Tarafından sağlanan bazı yöntemler atlandığını `ICorRuntimeHost`.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteApplication yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|ClickOnce dağıtım senaryolarında bildirimi tabanlı yeni bir etki alanına etkinleştirilmesi için uygulamayı belirtmek için kullanılır.|  
|[Executeınappdomain yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Belirtir <xref:System.AppDomain> belirtilen yönetilen kod yürütmek üzere.|  
|[Executeındefaultappdomain yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen derlemedeki belirtilen türe ait belirtilen yöntemi çağırır.|  
|[GetCLRControl yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Arabirim işaretçisi türü alır [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.|  
|[Getcurrentappdomainıd yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.|  
|[SetHostControl yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Ana bilgisayar denetim arabirimi ayarlar. Çağırmalısınız `SetHostControl` çağırmadan önce `Start`.|  
|[Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|CLR bir işlem başlatır.|  
|[Stop yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Kod yürütmeyi çalışma zamanı tarafından durdurur.|  
|[UnloadAppDomain yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcı karşılık gelir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], kullanın [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) gösteren bir işaretçi almak için arabirimi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirim ve ardından arama [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) gösteren bir işaretçi almak için yöntemi `ICLRRuntimeHost`. Önceki sürümlerde .NET Framework'ün, ana bilgisayar için bir işaretçi alır bir `ICLRRuntimeHost` çağırarak örneği [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Herhangi bir .NET Framework 2.0 sürümünde sağlanan teknolojileri uygulamaları sağlamak için kullanmalısınız `ICLRRuntimeHost` yerine `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Çağırmayın [Başlat](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) bildirimi tabanlı bir uygulama etkinleştirmek için yöntemi. Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Icorruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Clrruntimehost ortak sınıfı](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
