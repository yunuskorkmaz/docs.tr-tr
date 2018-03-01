---
title: ICLRMetaHost Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a12635e14b694b361e2877041588d7d9f08a4102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost Arabirimi
Kendi sürüm numarasına göre belirli bir sürümünü ortak dil çalışma zamanı (CLR) döndürür, tüm yüklü CLRs listesinde, belirtilen bir işlemde yüklenen tüm çalışma zamanları listesinde, bir derlemeyi derlemek, bir işlem çıkmak için kullanılan CLR sürümü Bul yöntemler sağlar bir çalışma zamanı temiz kapatma ve sorgu eski API bağlama ile.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Geçerli bir içeren bir numaralandırmayı döndüren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) bir bilgisayarda yüklü her bir CLR sürümü için arabirim işaretçisi.|  
|[EnumerateLoadedRuntimes Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Geçerli bir içeren bir numaralandırmayı döndüren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) belirli bir işlemde yüklü her CLR arabirimi işaretçisi. Bu yöntem yerini [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Tüm yüklenen çalışma zamanları dikkatlice kapatmak çalışır ve işlemi sonlandırır. Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.|  
|[GetRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Alır [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) belirli bir CLR sürümüne karşılık gelen arabirimi. Bu yöntem yerini [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ile kullanılan işlev [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağı.|  
|[GetVersionFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Dosya yoluna verilen (meta verilerde depolanan), derlemenin özgün .NET Framework derleme sürümünü alır. Bu yöntem yerini [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Eski etkinleştirme İlkesi bağlı, örneğin kullanarak bir çalışma zamanı temsil eden bir arabirim döndürür `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) doğrudan kullanılarak yapılandırma dosyası girişi eski etkinleştirme API'leri veya çağırarak [Iclrruntimeınfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi.|  
|[RequestRuntimeLoadedNotification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|CLR sürümü ilk yüklendi, ancak henüz başlamamış belirtilen işlev işaretçisi için bir geri çağırma güvence altına alır. Bu yöntem yerini [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim örneğini almak için tek çağırarak yoludur [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) gibi işlev:  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
