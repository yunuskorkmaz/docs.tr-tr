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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703657"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:  
  
- Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.  
  
- Tarafından sunulan bazı yöntemlerin atlanarak `ICorRuntimeHost` .  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ExecuteApplication Yöntemi](iclrruntimehost-executeapplication-method.md)|Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.|  
|[ExecuteInAppDomain Yöntemi](iclrruntimehost-executeinappdomain-method.md)|<xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.|  
|[ExecuteInDefaultAppDomain Yöntemi](iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.|  
|[GetCLRControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.|  
|[GetCurrentAppDomainId Yöntemi](iclrruntimehost-getcurrentappdomainid-method.md)|<xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.|  
|[SetHostControl Yöntemi](iclrruntimehost-sethostcontrol-method.md)|Konak denetim arabirimini ayarlar. `SetHostControl`Çağrılmadan önce öğesini çağırmanız gerekir `Start` .|  
|[Start yöntemi](iclrruntimehost-start-method.md)|CLR 'yi bir işlem olarak başlatır.|  
|[Stop Yöntemi](iclrruntimehost-stop-method.md)|Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.|  
|[UnloadAppDomain Yöntemi](iclrruntimehost-unloadappdomain-method.md)|<xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen öğesini kaldırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) arabirimini kullanarak [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve sonra bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodunu çağırın `ICLRRuntimeHost` . .NET Framework önceki sürümlerinde, konak `ICLRRuntimeHost` [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)çağırarak bir örneğe yönelik bir işaretçi alır. .NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için yerine kullanmanız gerekir `ICLRRuntimeHost` `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemini çağırmayın. `Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx İşlevi](corbindtoruntimeex-function.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [CLRRuntimeHost Coclass’ı](clrruntimehost-coclass.md)
