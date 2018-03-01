---
title: "CorBindToRuntimeEx İşlevi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c0080e5a01c8e856c2862182ba06096fdc9385c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx İşlevi
Ortak dil çalışma zamanı (CLR) süreç içine yüklemek için yönetilmeyen konakları etkinleştirir. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri gerçekleştirmek aynı işlemi ancak `CorBindToRuntimeEx` işlevi CLR davranışını belirtmek için bayrakları ayarlamanıza olanak sağlar.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Bu işlev, aşağıdakileri yapmak konak izin vermek parametreleri kümesini alır:  
  
-   Yüklenecek çalışma zamanı sürümü belirtin.  
  
-   Sunucu veya iş istasyonu yapı yüklü olup olmadığını gösterir.  
  
-   Eşzamanlı atık toplama veya eşzamansız atık toplama yapılır olup olmadığını denetler.  
  
> [!NOTE]
>  Eşzamanlı atık toplama WOW64 çalışan uygulamalarda desteklenmiyor x86 (eski adıyla IA-64) Intel Itanium mimarisi uygulama 64 bitlik sistemlerde öykünücüsü. 64-bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz: [çalıştıran 32-bit uygulamalar](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
-   Etki alanı bağımsız yüklenen derlemeleri olup olmadığını denetler.  
  
-   Bir arabirim işaretçisi elde bir [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) başlamadan önce CLR örneği yapılandırmak için ek seçenekleri ayarlamak için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 [in] Yüklemek istediğiniz CLR sürümü tanımlayan bir dize.  
  
 .NET Framework sürüm numarası noktalarla ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Dize olarak geçirilen `pwszVersion` sürüm numarası (örneğin, "v1.0.1529") ilk üç bölümleri tarafından izlenen "v" karakter ile başlamalıdır.  
  
 CLR bazı sürümleri CLR önceki sürümleriyle uyumluluk belirten bir ilke bildirimi ile yüklenir. Varsayılan olarak, başlatma dolgusu değerlendirir `pwszVersion` ilke deyimleri ve yükleri karşı çalışma zamanı en son sürümü olan istenen sürümü ile uyumlu. Bir ana bilgisayar ilkesi değerlendirmesi atlayın ve belirtilen tam sürümünü yüklemek için dolgu zorlayabilirsiniz `pwszVersion` değerini geçirerek `STARTUP_LOADER_SAFEMODE` için `startupFlags` aşağıda açıklandığı gibi parametre.  
  
 Arayan için null belirtiyorsa `pwszVersion`, `CorBindToRuntimeEx` yüklü olan sürüm numaraları .NET Framework 4 çalışma zamanı'den daha düşük ve en son sürümünü çalışma zamanı bu kümeden yükler çalışma zamanları kümesini tanımlar. Önceki bir sürümünü yüklediyseniz .NET Framework 4 veya üstünü ve başarısız yüklemez. Null geçirme ana bilgisayar üzerinde çalışma zamanı sürümü yüklendi denetimi verdiğini unutmayın. Bu yaklaşım bazı senaryolarda uygun olmakla birlikte, konak yüklemek için belirli bir sürümü sağlamanız önerilir.  
  
 `pwszBuildFlavor`  
 [in] Sunucu veya CLR iş istasyonu yapı yük belirtir bir dize. Geçerli değerler `svr` ve `wks`. Server yapı çöp koleksiyonları için birden çok işlemci yararlanmak için optimize edilmiştir ve iş istasyonu yapı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilmiştir.  
  
 Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derleme yüklenir. Bir tek işlemcili makine üzerinde çalışan iş istasyonu derleme her zaman yüklenir, olsa bile `pwszBuildFlavor` ayarlanır `svr`. Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı atık toplama belirtilir (açıklamasına bakın `startupFlags` parametresi), sunucu derleme yüklendi.  
  
 `startupFlags`  
 [in] Değerleri bir birleşimini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırması. Bu bayrakları eşzamanlı atık toplama, etki alanı Tarafsız kodu ve davranışını denetleyen `pwszVersion` parametresi. Hiçbir bayrağı ayarlandıysa, varsayılan tek etki alanıdır. Aşağıdaki değerler geçerlidir:  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Bu bayrakların açıklamaları için bkz: [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırması.  
  
 `rclsid`  
 [in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi. Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.  
  
 `riid`  
 [in] `IID` İstenen arabiriminden, `rclsid`. Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.  
  
 `ppv`  
 [out] Döndürülen arabirimi işaretçisi `riid`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `pwszVersion` yok, bir çalışma zamanı sürümü belirtir `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT değerini döndürür.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Yürütme bağlamı ve Windows Identity akışı  
 CLR 1 sürümünde <xref:System.Security.Principal.WindowsIdentity> nesne yeni iş parçacığı, iş parçacığı havuzları ya da Zamanlayıcı geri aramalar gibi zaman uyumsuz noktaları arasında akış değil. CLR 2.0 sürümünde bir <xref:System.Threading.ExecutionContext> nesne şu anda yürütülen iş parçacığı hakkında bazı bilgiler sarmalar ve herhangi bir zaman uyumsuz noktası arasında ancak uygulama etki alanı sınırları boyunca değil akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de hiçbir zaman uyumsuz noktası üzerinden akar. Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme varsa, çok akar.  
  
 İki yolla akış değiştirebilirsiniz:  
  
1.  Değiştirerek <xref:System.Threading.ExecutionContext> akışını bir iş parçacığı başına temelinde gizlemek için ayarları (bkz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).  
  
2.  Sürüm 1 uyumluluk moduna işlemi varsayılan modu değiştirerek nerede <xref:System.Security.Principal.WindowsIdentity> nesne akan tüm zaman uyumsuz noktası üzerinden bağımsız olarak, <xref:System.Threading.ExecutionContext> geçerli iş parçacığının ayarlar. Varsayılan modunu değiştirmek nasıl olup, yönetilen bir yürütülebilir dosya veya yönetilmeyen bir barındırma arabirimi CLR yüklemeye kullanmasına bağlı olarak değişir:  
  
    1.  Yönetilen yürütülebilir dosyalar için ayarlamanız gerekir `enabled` özniteliği [ \<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesine `true`.  
  
    2.  Barındırma arabirimleri yönetilmeyen ayarlamanız `STARTUP_LEGACY_IMPERSONATION` içinde bayrak `startupFlags` çağırırken parametre `CorBindToRuntimeEx` işlevi.  
  
     Sürüm 1 uyumluluk modu, tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
