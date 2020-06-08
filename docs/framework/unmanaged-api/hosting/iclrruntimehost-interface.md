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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504088"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost Arabirimi
.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:  
  
- Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.  
  
- Tarafından sunulan bazı yöntemlerin atlanarak `ICorRuntimeHost` .  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[ExecuteApplication Yöntemi](iclrruntimehost-executeapplication-method.md)|Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.|  
|[ExecuteInAppDomain Yöntemi](iclrruntimehost-executeinappdomain-method.md)|<xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.|  
|[ExecuteInDefaultAppDomain Yöntemi](iclrruntimehost-executeindefaultappdomain-method.md)|Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.|  
|[GetCLRControl Yöntemi](iclrruntimehost-getclrcontrol-method.md)|Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.|  
|[GetCurrentAppDomainId Yöntemi](iclrruntimehost-getcurrentappdomainid-method.md)|<xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.|  
|[SetHostControl Yöntemi](iclrruntimehost-sethostcontrol-method.md)|Konak denetim arabirimini ayarlar. `SetHostControl`Çağrılmadan önce öğesini çağırmanız gerekir `Start` .|  
|[Start yöntemi](iclrruntimehost-start-method.md)|CLR 'yi bir işlem olarak başlatır.|  
|[Stop Yöntemi](iclrruntimehost-stop-method.md)|Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.|  
|[UnloadAppDomain Yöntemi](iclrruntimehost-unloadappdomain-method.md)|<xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen öğesini kaldırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak [ICLRMetaHost](iclrmetahost-interface.md) arabirimini kullanarak [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve sonra bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) metodunu çağırın `ICLRRuntimeHost` . .NET Framework önceki sürümlerinde, konak `ICLRRuntimeHost` [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)çağırarak bir örneğe yönelik bir işaretçi alır. .NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için yerine kullanmanız gerekir `ICLRRuntimeHost` `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](iclrruntimehost-start-method.md) yöntemini çağırmayın. `Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.  
  
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
