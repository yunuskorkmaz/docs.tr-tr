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
ms.openlocfilehash: 5ed383f616770fa8bab8e7a8944fa0f922017d87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122960"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx İşlevi
Ortak dil çalışma zamanı (CLR) bir işleme yüklemek için yöneilmeyen ana bilgisayarları etkinleştirir. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) ve `CorBindToRuntimeEx` işlevleri gerçekleştiren aynı işlemi ancak `CorBindToRuntimeEx` işlevi CLR'nin davranışını belirtmek için bayrakları ayarlamanızı sağlar.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Bu işlev konak aşağıdakileri yapmasına izin vermek parametreleri kümesini alır:  
  
-   Yüklenecek çalışma zamanı sürümü belirtin.  
  
-   Sunucu veya iş istasyonunun derleme yüklü olup olmadığını gösterir.  
  
-   Eş zamanlı çöp toplama veya eşzamansız atık toplama yapılan olup olmadığını denetler.  
  
> [!NOTE]
>  Eş zamanlı çöp toplama, WOW64 çalışan uygulamalarda desteklenmez x86 Intel Itanium mimarisini (eski adıyla IA-64 olarak adlandırılmıştır) uygulayan 64 bitlik sistemlerde öykünücüsü. 64 bit Windows sistemlerinde WOW64 kullanma hakkında daha fazla bilgi için bkz. [çalışan 32-bit uygulamaları](/windows/desktop/WinProg64/running-32-bit-applications).  
  
-   Etki alanından bağımsız yüklenen derlemeleri olup olmadığını denetler.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 [in] Yüklemek istediğiniz CLR sürümünü tanımlayan dize.  
  
 .NET Framework uygulamasındaki sürüm numarası noktayla ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Olarak geçen dize `pwszVersion` (örneğin, "v1.0.1529") sürüm numarasının ilk üç parçalar tarafından izlenen "v" karakteriyle başlamalıdır.  
  
 CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle birlikte yüklenir. Varsayılan olarak, başlangıç dolgusu değerlendirir `pwszVersion` ilke bildirimlerine ve yükleri karşı çalışma zamanının en son sürümü olan istenen sürümle uyumlu. Bir konak ilke değerlendirmesini atlamaya ve belirtilen tam sürümü yüklemeye zorlayabilir `pwszVersion` değerini geçirerek `STARTUP_LOADER_SAFEMODE` için `startupFlags` aşağıda açıklandığı gibi parametre.  
  
 Arayan için null belirtiyorsa `pwszVersion`, `CorBindToRuntimeEx` yüklü olan sürüm numaraları, .NET Framework 4 çalışma zamanı düşüktür ve bu kümeden çalışma zamanının en son sürümünü yükler çalışma zamanları kümesini tanımlar. Önceki bir sürümü yüklü değilse .NET Framework 4 veya sonrasını ve başarısız yüklenmiyor. Null geçirme konak çalışma zamanının yüklendiği üzerinde hiçbir denetimi verdiğini unutmayın. Bu yaklaşım bazı senaryolarda uygun olsa da, konağın belirli bir sürümünü yüklemek için sağlamanız önerilir.  
  
 `pwszBuildFlavor`  
 [in] Sunucunun veya CLR çalışma istasyonu yapısı yükleneceğini belirten bir dize. Geçerli değerler `svr` ve `wks`. Sunucu yapısı çöp toplama için birden çok işlemciden yararlanmak için optimize edilmiştir ve çalışma istasyonu yapısı tek işlemcili makinede çalışan istemci uygulamaları için optimize edilmiştir.  
  
 Varsa `pwszBuildFlavor` ayarlamak null iş istasyonu derlemesi yüklenir. İş istasyonu yapısı, bir tek işlemcili makinede çalışırken daima yüklenir, bile `pwszBuildFlavor` ayarlanır `svr`. Ancak, varsa `pwszBuildFlavor` ayarlanır `svr` ve eş zamanlı çöp toplama belirtilmişse (açıklamasına bakın `startupFlags` parametresi), sunucu yapısı yüklenir.  
  
 `startupFlags`  
 [in] Değerlerinin bir birleşimini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi. Bu bayraklar eş zamanlı çöp toplama, alan-bağımsız kod ve davranışını denetleyen `pwszVersion` parametresi. Varsayılan, hiçbir bayrak ayarlanmışsa tek etki alanıdır. Aşağıdaki değerler geçerlidir:  
  
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
  
 Bu bayraklar açıklamaları için bkz. [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi.  
  
 `rclsid`  
 [in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi. Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.  
  
 `riid`  
 [in] `IID` , İstenen arabiriminden `rclsid`. Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.  
  
 `ppv`  
 [out] Döndürülen arabirim işaretçisi `riid`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `pwszVersion` mevcut değil, bir çalışma zamanı sürümünü belirten `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD bir HRESULT değerini döndürür.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Yürütme bağlamı ve Windows Identity akışı  
 CLR sürüm 1 <xref:System.Security.Principal.WindowsIdentity> nesne yeni iş parçacığı, iş parçacığı havuzları ya da Zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalar arasında akış değil. CLR 2.0 sürümünde bir <xref:System.Threading.ExecutionContext> nesne yürütülmekte olan iş parçacığını hakkında bazı bilgiler sarmalar ve herhangi bir zaman uyumsuz noktası arasında ancak olmayan uygulama etki alanı sınırları üzerinden akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesne de herhangi bir zaman uyumsuz noktası üzerinden akar. Bu nedenle, iş parçacığı üzerinde geçerli kimliğe bürünme varsa, çok akar.  
  
 Flow'a iki şekilde değiştirebilirsiniz:  
  
1.  Değiştirerek <xref:System.Threading.ExecutionContext> akışını bir iş parçacığı başına temelinde bastırmak için ayarları (bkz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemleri).  
  
2.  Sürüm 1 uyumluluk modu için varsayılan işlem modu değiştirerek burada <xref:System.Security.Principal.WindowsIdentity> nesne akan tüm zaman uyumsuz noktası üzerinden açmamasından <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde. Varsayılan mod nasıl değiştirmeniz mi yönetilen bir yürütülebilir dosya veya yönetilmeyen bir barındırma arabiriminin CLR'yi yüklemek için kullandığınıza bağlıdır:  
  
    1.  Yönetilen yürütülebilir dosyalar için ayarlamanız gerekir `enabled` özniteliği [ \<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesine `true`.  
  
    2.  Yönetilmeyen barındırma arabirimleri için ayarlanan `STARTUP_LEGACY_IMPERSONATION` bayrağını `startupFlags` çağırırken parametre `CorBindToRuntimeEx` işlevi.  
  
     Sürüm 1 uyumluluk modu, tüm işlem ve işlemde tüm uygulama etki alanları için geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
