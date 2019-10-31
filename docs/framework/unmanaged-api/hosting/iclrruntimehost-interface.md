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
ms.openlocfilehash: 568c63681b84d0ab3642d84e4a6715ad230582db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120388"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:  
  
- Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.  
  
- `ICorRuntimeHost`tarafından sunulan bazı yöntemlerin atlanarak.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteApplication Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.|  
|[ExecuteInAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Belirtilen yönetilen kodun çalıştırılacağı <xref:System.AppDomain> belirtir.|  
|[ExecuteInDefaultAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.|  
|[GetCLRControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.|  
|[GetCurrentAppDomainId Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Şu anda yürütülmekte olan <xref:System.AppDomain> sayısal tanımlayıcısını alır.|  
|[SetHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Konak denetim arabirimini ayarlar. `Start`çağrılmadan önce `SetHostControl` çağırmanız gerekir.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|CLR 'yi bir işlem olarak başlatır.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.|  
|[UnloadAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Belirtilen sayısal tanımlayıcıya karşılık gelen <xref:System.AppDomain> kaldırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) arabirimini kullanarak [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve `ICLRRuntimeHost`bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodunu çağırın. .NET Framework önceki sürümlerinde, konak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)çağırarak bir `ICLRRuntimeHost` örneğine yönelik bir işaretçi alır. .NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için `ICorRuntimeHost`yerine `ICLRRuntimeHost` kullanmanız gerekir.  
  
> [!IMPORTANT]
> Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemini çağırmayın. `Start` yöntemi ilk kez çağrılırsa, `ExecuteApplication` yöntemi çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
