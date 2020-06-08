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
ms.openlocfilehash: e66b63ffa4ed25e861cff6bd9eb6065f57ff807f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493506"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx İşlevi
Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar. [CorBindToRuntime](corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlevi clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
 Bu işlev, bir ana bilgisayarın aşağıdakileri yapmasına izin veren bir parametre kümesi alır:  
  
- Yüklenecek çalışma zamanının sürümünü belirtin.  
  
- Sunucu veya iş istasyonu derlemesinin yüklenip yüklenmeyeceğini belirtin.  
  
- Eşzamanlı atık toplama veya eşzamanlı olmayan çöp toplamanın gerçekleştirilip yapılmadığını denetleyin.  
  
> [!NOTE]
> Intel Itanium mimarisini (daha önce IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde WOW64 x86 öykünücüsünü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [32-bit uygulamaları çalıştırma](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Derlemelerin etki alanı nötr olarak yüklenip yüklenmediğini denetleyin.  
  
- Bir [ICorRuntimeHost](icorruntimehost-interface.md) için, başlamadan önce clr örneğini yapılandırmak için ek seçenekler ayarlamak üzere kullanılabilecek bir arabirim işaretçisi edinin.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
 .NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*. Geçirilen dize, `pwszVersion` "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").  
  
 CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç dolgusu `pwszVersion` ilke deyimlerine göre değerlendirilir ve çalışma zamanının istenen sürümle uyumlu olan en son sürümünü yükler. Bir ana bilgisayar, `pwszVersion` `STARTUP_LOADER_SAFEMODE` `startupFlags` aşağıda açıklandığı gibi, bu dolgunun ilke değerlendirmesini atlamasını ve parametresi için bir değer geçirerek belirtilen tam sürümü yüklemesini zorlayabilir.  
  
 Çağıran için null belirtiyorsa `pwszVersion` , `CorBindToRuntimeEx` sürüm numaraları .NET Framework 4 çalışma zamanından daha düşük olan yüklü çalışma zamanları kümesini tanımlar ve bu kümeden çalışma zamanının en son sürümünü yükler. .NET Framework 4 veya sonraki bir sürümü yüklemez ve eski sürüm yüklenmemişse başarısız olur. Null geçirildiğine, ana bilgisayarın hangi çalışma zamanının sürümünün yüklü olmadığını belirten bir denetim verilmiştir. Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.  
  
 `pwszBuildFlavor`  
 'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize. Geçerli değerler `svr` ve ' dir `wks` . Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.  
  
 `pwszBuildFlavor`Null olarak ayarlanırsa, iş istasyonu derlemesi yüklenir. Tek işlemcili bir makinede çalışırken, olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir `pwszBuildFlavor` `svr` . Ancak, `pwszBuildFlavor` olarak ayarlanmışsa `svr` ve eşzamanlı çöp toplama belirtilirse (parametresinin açıklamasına bakın `startupFlags` ), sunucu derlemesi yüklenir.  
  
 `startupFlags`  
 'ndaki [Startup_flags](startup-flags-enumeration.md) numaralandırması değerlerinin birleşimi. Bu bayraklar, eşzamanlı atık toplamayı, etki alanını bağımsız kodu ve parametresinin davranışını denetler `pwszVersion` . Hiçbir bayrak ayarlanmamışsa varsayılan, tek etki alanıdır. Aşağıdaki değerler geçerlidir:  
  
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
  
 Bu bayrakların açıklamaları için [startup_flags](startup-flags-enumeration.md) sabit listesine bakın.  
  
 `rclsid`  
 'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki `IID`İçindeki istenen arabirimin `rclsid` . Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Döndürülen arabirim işaretçisi `riid` .  
  
## <a name="remarks"></a>Açıklamalar  
 `pwszVersion`Mevcut olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Windows kimliğinin yürütme bağlamı ve akışı  
 CLR sürüm 1 ' de, nesne, <xref:System.Security.Principal.WindowsIdentity> yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalarda akış yapmaz. CLR sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne Ayrıca herhangi bir zaman uyumsuz noktada akar. Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.  
  
 Akışı iki şekilde değiştirebilirsiniz:  
  
1. <xref:System.Threading.ExecutionContext>Her iş parçacığı temelinde akışı bastırmak için ayarları değiştirerek (bkz.,, <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).  
  
2. İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki ayarlardan bağımsız olarak nesnenin herhangi bir zaman uyumsuz noktada akış yapmaz. Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:  
  
    1. Yönetilen yürütülebilir dosyalar için, `enabled` öğesinin özniteliğini olarak ayarlamanız gerekir [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .  
  
    2. Yönetilmeyen barındırma arabirimleri için, `STARTUP_LEGACY_IMPERSONATION` `startupFlags` işlevini çağırırken parametresindeki bayrağı ayarlayın `CorBindToRuntimeEx` .  
  
     Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost İşlevi](corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
