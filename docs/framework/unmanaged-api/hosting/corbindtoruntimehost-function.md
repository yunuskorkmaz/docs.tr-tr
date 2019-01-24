---
title: CorBindToRuntimeHost İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c65b0f2b91527d7cd2c1ef2eba607bbd477571e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699460"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost İşlevi
Bir işleme belirtilen bir ortak dil çalışma zamanı (CLR) sürümünü yüklemek için ana bilgisayarları etkinleştirir.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
 [in] Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.  
  
 .NET Framework uygulamasındaki sürüm numarası noktayla ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Olarak geçen dize `pwszVersion` (örneğin, "v1.0.1529") sürüm numarasının ilk üç parçalar tarafından izlenen "v" karakteriyle başlamalıdır.  
  
 CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle birlikte yüklenir. Varsayılan olarak, başlangıç dolgusu değerlendirir `pwszVersion` ilke bildirimlerine ve yükleri karşı çalışma zamanının en son sürümü olan istenen sürümle uyumlu. Bir konak ilke değerlendirmesini atlamaya ve belirtilen tam sürümü yüklemeye zorlayabilir `pwszVersion` STARTUP_LOADER_SAFEMODE değerini geçirerek `startupFlags` parametresi.  
  
 Varsa `pwszVersion` olduğu `null,` yöntem CLR'nin herhangi bir sürümünü yüklemez. Bunun yerine çalışma zamanının başarısız olduğunu gösteren CLR_E_SHIM_RUNTIMELOAD döndürür.  
  
 `pwszBuildFlavor`  
 [in] Sunucunun veya CLR çalışma istasyonu yapısı yükleneceğini belirten bir dize. Geçerli değerler `svr` ve `wks`. Sunucu yapısı çöp toplama için birden çok işlemciden yararlanmak için optimize edilmiştir ve çalışma istasyonu yapısı tek işlemcili makinede çalışan istemci uygulamaları için optimize edilmiştir.  
  
 Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derlemesi yüklenir. İş istasyonu yapısı, bir tek işlemcili makinede çalışırken daima yüklenir, bile `pwszBuildFlavor` ayarlanır `svr`. Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eş zamanlı çöp toplama belirtilmişse (açıklamasına bakın `startupFlags` parametresi), sunucu yapısı yüklenir.  
  
> [!NOTE]
>  Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [in] Yüklenecek CLR sürümünü belirten ana bilgisayar yapılandırma dosyasının adı. Dosya adı tam nitelenmiş bir yol içermiyorsa, dosyanın çağrıyı yapan yürütülebilir olarak aynı dizinde olduğu varsayılır.  
  
 `pReserved`  
 [in] Sonra genişletilebilmek için ayrılmış.  
  
 `startupFlags`  
 [in] Eş zamanlı çöp toplama, alan-bağımsız kod ve davranışını denetleyen bayrak kümesi `pwszVersion` parametresi. Varsayılan, hiçbir bayrak ayarlanmışsa tek etki alanıdır. Desteklenen değerler listesi için bkz. [STARTUP_FLAGS numaralandırma](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi. Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.  
  
 `riid`  
 [in] `IID` Arabirimin istiyorsunuz. Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.  
  
 `ppv`  
 [out] Yüklenen çalışma zamanı sürümü için bir arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
