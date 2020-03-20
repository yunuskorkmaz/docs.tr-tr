---
title: CorBindToRuntime İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176519"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime İşlevi
Yönetilmeyen ana bilgisayarların ortak dil çalışma süresini (CLR) bir işleme yüklemesini sağlar.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwszVersion`  
 [içinde] Yüklemek istediğiniz CLR sürümünü açıklayan bir dize.  
  
 .NET Framework'deki bir sürüm numarası dönemlere göre ayrılmış dört bölümden oluşur: *major.minor.build.revision*. Dize olarak `pwszVersion` "v" karakteri ve ardından sürüm numarasının ilk üç bölümü (örneğin, "v1.0.1529" ile başlamak gerekir) ile geçildi.  
  
 CLR'nin bazı sürümleri, CLR'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç şimi `pwszVersion` ilke deyimlerine göre değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler. Bir ana bilgisayar, şimi ilke değerlendirmesini atlamaya `pwszVersion` ve aşağıda `STARTUP_LOADER_SAFEMODE` açıklandığı `flags` gibi parametre için bir değer geçirerek belirtilen tam sürümü yüklemeye zorlayabilir.  
  
 Arayan için `pwszVersion`null belirtirse, çalışma zamanının en son sürümü yüklenir. Null'u geçmek, ana bilgisayara çalışma zamanının hangi sürümünün yüklendiği üzerinde hiçbir denetim vermez. Bu yaklaşım bazı senaryolarda uygun olsa da, ana bilgisayara yüklemek için belirli bir sürüm sağlaması önerilir.  
  
 `pwszBuildFlavor`  
 [içinde] Sunucuyu veya CLR'nin iş istasyonu oluşturmasını yükleyip yükleymeyeceğini belirten bir dize. Geçerli değerler `svr` `wks`ve . Sunucu yapısı çöp koleksiyonları için birden çok işlemciden yararlanacak şekilde optimize edilse de, iş istasyonu yapısı tek işlemcili bir makinede çalışan istemci uygulamaları için optimize edilsin.  
  
 Null `pwszBuildFlavor` ayarlanırsa, iş istasyonu yapısı yüklenir. Tek işlemcili bir makinede çalışırken, iş istasyonu yapısı `pwszBuildFlavor` her zaman `svr`yüklenir, buna göre ayarlanmış olsa bile. Ancak, `pwszBuildFlavor` ayarlanır `svr` ve eşzamanlı çöp toplama belirtilirse `flags` (parametreaçıklamasına bakın), sunucu yapısı yüklenir.  
  
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
  
    2. Yönetilmeyen barındırma arabirimleri `STARTUP_LEGACY_IMPERSONATION` `flags` `CorBindToRuntimeEx` için, işlevi ararken parametredeki bayrağı ayarlayın.  
  
     Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` ve aynı işlemi gerçekleştirmek, ancak `CorBindToRuntimeEx` işlev CLR davranışını belirtmek için bayrakları ayarlamanızı sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
