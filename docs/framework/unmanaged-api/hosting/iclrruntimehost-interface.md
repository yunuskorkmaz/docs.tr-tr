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
ms.openlocfilehash: 95dd084520d1e93803a91f0c4d01214ed0d3744d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436247"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
Benzer işlevsellik sağlar [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework sürüm 1, aşağıdaki değişiklikleri ile sağlanan arabirim:  
  
-   Eklenmesi [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) ana denetim arabirimi ayarlamak için yöntem.  
  
-   Tarafından sağlanan bazı yöntemler atlandığını `ICorRuntimeHost`.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteApplication Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|ClickOnce dağıtım senaryolarında bildirimi tabanlı yeni bir etki alanına etkinleştirilmesi için uygulamayı belirtmek için kullanılır.|  
|[ExecuteInAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Belirtir <xref:System.AppDomain> belirtilen yönetilen kod yürütmek üzere.|  
|[ExecuteInDefaultAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen derlemedeki belirtilen türe ait belirtilen yöntemi çağırır.|  
|[GetCLRControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Arabirim işaretçisi türü alır [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.|  
|[GetCurrentAppDomainId Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.|  
|[SetHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Ana bilgisayar denetim arabirimi ayarlar. Çağırmalısınız `SetHostControl` çağırmadan önce `Start`.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|CLR bir işlem başlatır.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Kod yürütmeyi çalışma zamanı tarafından durdurur.|  
|[UnloadAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcı karşılık gelir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], kullanın [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) gösteren bir işaretçi almak için arabirimi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirim ve ardından arama [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) gösteren bir işaretçi almak için yöntemi `ICLRRuntimeHost`. Önceki sürümlerde .NET Framework'ün, ana bilgisayar için bir işaretçi alır bir `ICLRRuntimeHost` çağırarak örneği [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Herhangi bir .NET Framework 2.0 sürümünde sağlanan teknolojileri uygulamaları sağlamak için kullanmalısınız `ICLRRuntimeHost` yerine `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Çağırmayın [Başlat](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) bildirimi tabanlı bir uygulama etkinleştirmek için yöntemi. Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CLRRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
