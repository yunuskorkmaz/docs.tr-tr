---
title: "CorBindToRuntimeHost İşlevi"
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
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6d69f39aa74665843b0bf91407e764ea67f41d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost İşlevi
Süreç içine ortak dil çalışma zamanı (CLR) belirtilen bir sürümünü yüklemek ana bilgisayarları sağlar.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 [in] Yüklemek istediğiniz CLR sürümü tanımlayan bir dize.  
  
 .NET Framework sürüm numarası noktalarla ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Dize olarak geçirilen `pwszVersion` sürüm numarası (örneğin, "v1.0.1529") ilk üç bölümleri tarafından izlenen "v" karakter ile başlamalıdır.  
  
 CLR bazı sürümleri CLR önceki sürümleriyle uyumluluk belirten bir ilke bildirimi ile yüklenir. Varsayılan olarak, başlatma dolgusu değerlendirir `pwszVersion` ilke deyimleri ve yükleri karşı çalışma zamanı en son sürümü olan istenen sürümü ile uyumlu. Bir ana bilgisayar ilkesi değerlendirmesi atlayın ve belirtilen tam sürümünü yüklemek için dolgu zorlayabilirsiniz `pwszVersion` için STARTUP_LOADER_SAFEMODE değerini geçirerek `startupFlags` parametresi.  
  
 Varsa `pwszVersion` olan `null,` yöntemi herhangi bir CLR sürümü yüklemez. Bunun yerine, çalışma zamanı yükleme başarısız olduğunu gösteren CLR_E_SHIM_RUNTIMELOAD döndürür.  
  
 `pwszBuildFlavor`  
 [in] Sunucu veya CLR iş istasyonu yapı yük belirtir bir dize. Geçerli değerler `svr` ve `wks`. Server yapı çöp koleksiyonları için birden çok işlemci yararlanmak için optimize edilmiştir ve iş istasyonu yapı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilmiştir.  
  
 Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derleme yüklenir. Bir tek işlemcili makine üzerinde çalışan iş istasyonu derleme her zaman yüklenir, olsa bile `pwszBuildFlavor` ayarlanır `svr`. Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı atık toplama belirtilir (açıklamasına bakın `startupFlags` parametresi), sunucu derleme yüklendi.  
  
> [!NOTE]
>  Eşzamanlı atık toplama WOW64 çalışan uygulamalarda desteklenmiyor x86 (eski adıyla IA-64) Intel Itanium mimarisi uygulama 64 bitlik sistemlerde öykünücüsü. 64-bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz: [çalıştıran 32-bit uygulamalar](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
 `pwszHostConfigFile`  
 [in] Yüklemek için CLR sürümü belirten bir ana bilgisayar yapılandırma dosyası adı. Dosya adı tam nitelenmiş bir yol içermiyorsa, dosyanın çağrıyı yapan yürütülebilir dosya ile aynı dizinde olduğu varsayılır.  
  
 `pReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış.  
  
 `startupFlags`  
 [in] Eşzamanlı atık toplama, etki alanı Tarafsız kodu ve davranışını denetleyen bayrakları kümesi `pwszVersion` parametresi. Hiçbir bayrağı ayarlandıysa, varsayılan tek etki alanıdır. Desteklenen değerler listesi için bkz: [STARTUP_FLAGS numaralandırması](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi. Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.  
  
 `riid`  
 [in] `IID` İsteyen arabirimi. Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.  
  
 `ppv`  
 [out] Yüklenen çalışma zamanı sürümü için bir arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
