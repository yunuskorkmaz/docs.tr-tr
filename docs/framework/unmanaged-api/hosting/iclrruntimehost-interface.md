---
title: ICLRRuntimeHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed32fe643a7722eaf1af38e6079096194690e950
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211405"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
Benzer işlevlere [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework sürüm 1'i aşağıdaki değişikliklerle birlikte sağlanan arabirim:  
  
-   Ek [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) konak denetimi arabirimi ayarlamak için yöntemi.  
  
-   Tarafından sağlanan bazı yöntemler Java'daki `ICorRuntimeHost`.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteApplication Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|ClickOnce dağıtım senaryolarında bildirim tabanlı yeni bir etki alanı etkinleştirilmesi için uygulamayı belirtmek için kullanılır.|  
|[ExecuteInAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Belirtir <xref:System.AppDomain> burada belirtilen yönetilen kodu yürütmek.|  
|[ExecuteInDefaultAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen bütünleştirilmiş kod içinde belirtilen türün belirtilen yöntemi çağırır.|  
|[GetCLRControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Türü bir arabirim işaretçisi alır [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.|  
|[GetCurrentAppDomainId Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.|  
|[SetHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Konak denetimi arabirimini ayarlar. Çağırmalısınız `SetHostControl` çağırmadan önce `Start`.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|CLR'yi bir işleme başlatır.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Çalışma zamanı tarafından kodun yürütülmesini durdurur.|  
|[UnloadAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcısına karşılık gelir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], kullanın [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) işaretçisi almak için arabirimi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirim ve sonra çağrı [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) işaretçisi almak için yöntemi `ICLRRuntimeHost`. Önceki .NET Framework sürümlerinde, konak için bir işaretçi alır. bir `ICLRRuntimeHost` çağırarak örneği [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). .NET Framework 2.0 sürümünde sağlanan teknolojilerin hiçbiri uygulamaları sağlamak için kullanmanız gerekir `ICLRRuntimeHost` yerine `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Çağırmayın [Başlat](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemi. Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost Coclass’ı](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
