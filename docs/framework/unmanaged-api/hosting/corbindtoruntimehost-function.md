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
ms.openlocfilehash: afb25ad9e1760f390aa8dfb3e1de39ea60f185c2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616625"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost İşlevi
Ana bilgisayarların belirli bir ortak dil çalışma zamanı (CLR) sürümünü bir işleme yüklemesine olanak sağlar.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.  
  
 .NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*. Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").  
  
 CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler. Bir konak, bu dolgunun ilke değerlendirmesini atlamasını ve ' de `pwszVersion` parametre için bir STARTUP_LOADER_SAFEMODE değeri geçirerek belirtilen tam sürümü yüklemesini zorunlu hale getirebilirsiniz `startupFlags` .  
  
 `pwszVersion`, `null,` Yöntemi clr 'nin herhangi bir sürümünü yüklemez. Bunun yerine, çalışma zamanını yükleyemediğini belirten CLR_E_SHIM_RUNTIMELOAD döndürür.  
  
 `pwszBuildFlavor`  
 'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize. Geçerli değerler `svr` ve ' dir `wks` . Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.  
  
 `pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir. Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` . Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `startupFlags` ), sunucu derlemesi yüklenir.  
  
> [!NOTE]
> Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 'ndaki Yüklenecek CLR sürümünü belirten bir ana bilgisayar yapılandırma dosyasının adı. Dosya adı tam nitelikli bir yol içermiyorsa, dosyanın çağrıyı yapan çalıştırılabilirle aynı dizinde olduğu varsayılır.  
  
 `pReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `startupFlags`  
 'ndaki Eşzamanlı çöp toplamayı, etki alanını bağımsız kodu ve parametresinin davranışını denetleyen bir bayrak kümesi `pwszVersion` . Hiçbir bayrak ayarlanmamışsa varsayılan, tek etki alanıdır. Desteklenen değerlerin listesi için bkz. [startup_flags numaralandırması](startup-flags-enumeration.md).  
  
 `rclsid`  
 'ndaki `CLSID` [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki `IID`İstediğiniz arabirim. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Yüklenen çalışma zamanının sürümüne yönelik bir arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](corbindtoruntimeex-function.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
