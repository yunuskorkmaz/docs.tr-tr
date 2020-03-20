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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176493"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost İşlevi
Ana bilgisayarların ortak dil çalışma zamanının (CLR) belirli bir sürümünü bir işleme yüklemesini sağlar.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 [içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.  
  
 .NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.  
  
 CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler. Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve parametre için `startupFlags` STARTUP_LOADER_SAFEMODE değerini geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.  
  
 Yöntem `pwszVersion` `null,` ise CLR herhangi bir sürümünü yüklemez. Bunun yerine, çalışma süresini yüklemeyi başaramadıCLR_E_SHIM_RUNTIMELOAD döndürür.  
  
 `pwszBuildFlavor`  
 [içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize. Geçerli değerler `svr` `wks`ve . Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.  
  
 Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir. Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile. Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `startupFlags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.  
  
> [!NOTE]
> Intel Itanium mimarisini (eski adıyla IA-64) uygulayan 64 bit sistemlerde WOW64 x86 emülatörü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için [32 bit Uygulamaları Çalıştırma'ya](/windows/desktop/WinProg64/running-32-bit-applications)bakın.  
  
 `pwszHostConfigFile`  
 [içinde] ClR'nin yüklenmesi için sürümünü belirten bir ana bilgisayar yapılandırma dosyasının adı. Dosya adı tam nitelikli bir yol içermiyorsa, dosyanın aramayı yapan yürütülebilir ile aynı dizinde olduğu varsayılır.  
  
 `pReserved`  
 [içinde] Gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `startupFlags`  
 [içinde] Eşzamanlı çöp toplama, etki alanı nötr kod ve `pwszVersion` parametre davranışını kontrol eden bayraklar kümesi. Bayrak ayarlıdeğilse varsayılan değer tek alan adıdır. Desteklenen değerlerin listesi için [numaralandırmaSTARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)bakın.  
  
 `rclsid`  
 [içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 [içinde] `IID` İstediğinin arayüzü. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 [çıkış] Yüklenen çalışma zamanı sürümüne bir arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.idl  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
