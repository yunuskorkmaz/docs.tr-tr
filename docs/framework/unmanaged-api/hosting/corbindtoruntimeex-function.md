---
title: CorBindToRuntimeEx İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f31ae29efee9b353c2dcc679724db73da5444e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969422"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx İşlevi
Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri aynı `CorBindToRuntimeEx` işlemi gerçekleştirir, ancak işlevi clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
 Bu işlev, bir ana bilgisayarın aşağıdakileri yapmasına izin veren bir parametre kümesi alır:  
  
- Yüklenecek çalışma zamanının sürümünü belirtin.  
  
- Sunucu veya iş istasyonu derlemesinin yüklenip yüklenmeyeceğini belirtin.  
  
- Eşzamanlı atık toplama veya eşzamanlı olmayan çöp toplamanın gerçekleştirilip yapılmadığını denetleyin.  
  
> [!NOTE]
> Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Derlemelerin etki alanı nötr olarak yüklenip yüklenmediğini denetleyin.  
  
- Bir [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) için, başlamadan önce clr örneğini yapılandırmak için ek seçenekler ayarlamak üzere kullanılabilecek bir arabirim işaretçisi edinin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.  
  
 .NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*. Geçirilen `pwszVersion` dize, "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").  
  
 CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç dolgusu ilke deyimlerine göre değerlendirilir `pwszVersion` ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler. Bir ana bilgisayar, aşağıda açıklandığı gibi, bu dolgunun ilke değerlendirmesini atlamasını ve `pwszVersion` `startupFlags` parametresi `STARTUP_LOADER_SAFEMODE` için bir değer geçirerek belirtilen tam sürümü yüklemesini zorlayabilir.  
  
 Çağıran için `pwszVersion`null belirtiyorsa, `CorBindToRuntimeEx` sürüm numaraları .NET Framework 4 çalışma zamanından daha düşük olan yüklü çalışma zamanları kümesini tanımlar ve bu kümeden çalışma zamanının en son sürümünü yükler. .NET Framework 4 veya sonraki bir sürümü yüklemez ve eski sürüm yüklenmemişse başarısız olur. Null geçirildiğine, ana bilgisayarın hangi çalışma zamanının sürümünün yüklü olmadığını belirten bir denetim verilmiştir. Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.  
  
 `pwszBuildFlavor`  
 'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize. Geçerli değerler ve `svr` ' `wks`dir. Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.  
  
 `pwszBuildFlavor` Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir. Tek işlemcili bir makinede çalışırken, olarak `pwszBuildFlavor` `svr`ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir. Ancak, `pwszBuildFlavor` olarak `svr` ayarlanmışsa ve eşzamanlı çöp toplama belirtilirse ( `startupFlags` parametresinin açıklamasına bakın), sunucu derlemesi yüklenir.  
  
 `startupFlags`  
 'ndaki [Startup_flags](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırması değerlerinin birleşimi. Bu bayraklar, eşzamanlı atık toplamayı, etki alanını bağımsız kodu ve `pwszVersion` parametresinin davranışını denetler. Hiçbir bayrak ayarlanmamışsa varsayılan, tek etki alanıdır. Aşağıdaki değerler geçerlidir:  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Bu bayrakların açıklamaları için bkz. [startup_flags](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi.  
  
 `rclsid`  
 'ndaki ICorRuntimeHost veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass. [](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) `CLSID` Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki `IID` İçindeki`rclsid`istenen arabirimin. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Döndürülen arabirim işaretçisi `riid`.  
  
## <a name="remarks"></a>Açıklamalar  
 Mevcut olmayan bir çalışma zamanı sürümü `CorBindToRuntimeEx` belirtiyorsa,CLR_E_SHIM_RUNTIMELOADiçinbirHRESULTdeğeridöndürür.`pwszVersion`  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Windows kimliğinin yürütme bağlamı ve akışı  
 CLR sürüm 1 ' de, <xref:System.Security.Principal.WindowsIdentity> nesne, yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalarda akış yapmaz. CLR sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne Ayrıca herhangi bir zaman uyumsuz noktada akar. Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.  
  
 Akışı iki şekilde değiştirebilirsiniz:  
  
1. Her iş parçacığı <xref:System.Threading.ExecutionContext> temelinde akışı bastırmak için ayarları değiştirerek ( <xref:System.Threading.ExecutionContext.SuppressFlow%2A>bkz <xref:System.Security.SecurityContext.SuppressFlow%2A>.,, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).  
  
2. İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> ayarlardan bağımsız olarak nesnenin herhangi bir zaman uyumsuz noktada akış yapmaz. Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:  
  
    1. Yönetilen yürütülebilir dosyalar için, `enabled` [ \<legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin özniteliğini olarak `true`ayarlamanız gerekir.  
  
    2. Yönetilmeyen barındırma arabirimleri için, `STARTUP_LEGACY_IMPERSONATION` `CorBindToRuntimeEx` işlevini çağırırken `startupFlags` parametresindeki bayrağı ayarlayın.  
  
     Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MSCorEE. h  
  
 **Kitaplığı** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
