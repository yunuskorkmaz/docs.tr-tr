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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176506"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx İşlevi
Yönetilmeyen ana bilgisayarların ortak dil çalışma süresini (CLR) bir işleme yüklemesini sağlar. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` işlev CLR davranışını belirtmek için bayrakları ayarlamanızı sağlar.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
 Bu işlev, bir ana bilgisayar aşağıdakileri yapmasına izin veren bir dizi parametre alır:  
  
- Yüklenecek çalışma zamanının sürümünü belirtin.  
  
- Sunucu veya iş istasyonu yapısının yüklenip yüklenmemesi gerektiğini belirtin.  
  
- Eşzamanlı çöp toplama veya eşzamanlı olmayan çöp toplama yapılıp yapılmadığını denetler.  
  
> [!NOTE]
> Intel Itanium mimarisini (eski adıyla IA-64) uygulayan 64 bit sistemlerde WOW64 x86 emülatörü çalıştıran uygulamalarda eşzamanlı çöp toplama desteklenmez. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için [32 bit Uygulamaları Çalıştırma'ya](/windows/desktop/WinProg64/running-32-bit-applications)bakın.  
  
- Derlemelerin etki alanı nötr olarak yüklenip yüklenmediğini denetle.  
  
- Başlatılmadan önce CLR'nin bir örneğini yapılandırmak için ek seçenekler ayarlamak için kullanılabilecek bir [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi işaretçisi edinin.  
  
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
 [içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.  
  
 .NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.  
  
 CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler. Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve aşağıda `STARTUP_LOADER_SAFEMODE` açıklandığı `startupFlags` gibi parametre için bir değer geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.  
  
 Arayan için null `pwszVersion`belirtirse, `CorBindToRuntimeEx` sürüm numaraları .NET Framework 4 çalışma zamanından daha düşük olan yüklü çalışma süreleri kümesini tanımlar ve çalışma zamanının en son sürümünü bu kümeden yükler. .NET Framework 4 veya sonraki yüklenmez ve önceki sürüm yüklenmezse başarısız olur. Null'u geçmek, ana bilgisayara çalışma zamanının hangi sürümünün yüklendiği üzerinde denetim vermez. Bu yaklaşım bazı senaryolarda uygun olsa da, ana bilgisayara yüklemek için belirli bir sürüm sağlaması önerilir.  
  
 `pwszBuildFlavor`  
 [içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize. Geçerli değerler `svr` `wks`ve . Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.  
  
 Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir. Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile. Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `startupFlags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.  
  
 `startupFlags`  
 [içinde] [numaralandırma STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) değerlerinin birleşimi. Bu bayraklar eşzamanlı çöp toplama, etki alanı nötr `pwszVersion` kodu ve parametredavranışını denetler. Bayrak ayarlıdeğilse varsayılan değer tek alan adıdır. Aşağıdaki değerler geçerlidir:  
  
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
  
 Bu bayrakların açıklamaları için [numaralandırmanın STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bakın.  
  
 `rclsid`  
 [içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 [içinde] İstenen `IID` arabirimin `rclsid`. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 [çıkış] Döndürülen arabirim `riid`işaretçisi .  
  
## <a name="remarks"></a>Açıklamalar  
 Var `pwszVersion` olmayan bir çalışma zamanı sürümü belirtirse, `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD Bir HRESULT değeri döndürür.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Yürütme Bağlamı ve Windows Kimliğinin Akışı  
 CLR'nin sürüm <xref:System.Security.Principal.WindowsIdentity> 1'inde, nesne yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri aramaları gibi eşzamanlı noktalar arasında akmaz. CLR'nin sürüm 2.0'ında, bir <xref:System.Threading.ExecutionContext> nesne şu anda çalıştırılamakta olan iş parçacığı yla ilgili bazı bilgileri sarar ve uygulama etki alanı sınırları boyunca değil, herhangi bir eşzamanlı nokta boyunca akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir asynchronous noktası boyunca akar. Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme, varsa, çok akar.  
  
 Akışı iki şekilde değiştirebilirsiniz:  
  
1. İş parçacığı <xref:System.Threading.ExecutionContext> başına akışı bastırmak için ayarları değiştirerek (bkz. <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>  
  
2. İşlem varsayılan modunu, geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> ayarlardan bağımsız olarak nesnenin herhangi bir eşyoknom noktası boyunca akmayan sürüm 1 uyumluluk moduna değiştirerek. Varsayılan modu nasıl değiştirdiğiniz, CLR'yi yüklemek için yönetilen bir yürütülebilir veya yönetilmeyen bir barındırma arabirimi kullanıp kullanmadığınıza bağlıdır:  
  
    1. Yönetilen yürütülebilir ler için `enabled` [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin özniteliğini `true`.  
  
    2. Yönetilmeyen barındırma arabirimleri `STARTUP_LEGACY_IMPERSONATION` `startupFlags` `CorBindToRuntimeEx` için, işlevi ararken parametredeki bayrağı ayarlayın.  
  
     Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
