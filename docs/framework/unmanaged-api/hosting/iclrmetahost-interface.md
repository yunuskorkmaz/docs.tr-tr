---
title: ICLRMetaHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45089d1b64264e000c07603808f0c5fb1263b042
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776576"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost Arabirimi
Kendi sürüm numarasına göre belirli bir sürümü ortak dil çalışma zamanı (CLR) döndürür, tüm yüklü CLRs listesinde, belirtilen bir işlemde yüklenen tüm çalışma zamanları listesinde, bir derlemeye derlemek, bir işleminden çıkmak için kullanılan CLR sürümü bulmak için yöntemler sağlar bir temiz çalışma zamanı kapatması ve sorgu eski API bağlama.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) bir bilgisayarda yüklü her bir CLR sürümü için arabirim işaretçisi.|  
|[EnumerateLoadedRuntimes Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) yüklenen verilen bir işlemde her CLR için arabirim işaretçisi. Bu yöntem yerine geçer [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Yüklenen tüm çalışma zamanları düzgün biçimde kapatılamadı dener ve sonra da işlemi sonlandırır. Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.|  
|[GetRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Alır [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) belirli bir CLR sürümüne karşılık gelen arabirimi. Bu yöntem yerine geçer [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ile kullanılan işlev [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağı.|  
|[GetVersionFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Verilen dosya yoluna (meta verilerinde depolanır), derlemenin özgün .NET Framework derleme sürümü alır. Bu yöntem yerine geçer [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Eski etkinleştirme İlkesi bağlı, örneğin kullanarak bir çalışma zamanı temsil eden bir arabirim döndürür `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) doğrudan kullanılarak yapılandırma dosyası girdisi eski etkinleştirme API'leri veya çağırarak [Iclrruntimeınfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi.|  
|[RequestRuntimeLoadedNotification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Bir CLR sürümü ilk yüklendi, ancak henüz başlatılmadı belirtilen işlev işaretçisi için bir geri çağırma garanti eder. Bu yöntem yerine geçer [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim örneğini almak için tek çağırarak yoludur [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) gibi işlev:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
