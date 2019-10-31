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
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138303"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime İşlevi
Yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) bir işleme yüklemesini sağlar.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
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
 'ndaki Yüklemek istediğiniz CLR sürümünü tanımlayan bir dize.  
  
 .NET Framework bir sürüm numarası, noktalarla ayrılmış dört bölümden oluşur: *ana. ikincil. derleme. düzeltme*. `pwszVersion` olarak geçirilen dize "v" karakteriyle başlamalı ve ardından sürüm numarasının ilk üç bölümü gelmelidir (örneğin, "v 1.0.1529").  
  
 CLR 'nin bazı sürümleri, CLR 'nin önceki sürümleriyle uyumluluğu belirten bir ilke bildirimiyle yüklenir. Varsayılan olarak, başlangıç dolgusu ilke deyimlerine karşı `pwszVersion` değerlendirir ve istenen sürümle uyumlu çalışma zamanının en son sürümünü yükler. Bir ana bilgisayar, aşağıda açıklandığı gibi `flags` parametresi için bir `STARTUP_LOADER_SAFEMODE` değeri geçirerek, dolgunun ilke değerlendirmesini atlayıp `pwszVersion` belirtilen tam sürümü yüklemesine zorlayabilir.  
  
 Arayan `pwszVersion`için null belirtiyorsa, çalışma zamanının en son sürümü yüklenir. Null geçirme, konağa çalışma zamanının hangi sürümünün yüklendiği üzerine bir denetim sağlar. Bu yaklaşım bazı senaryolarda uygun olabilir, ancak konağın yüklemek için belirli bir sürüm sağlaması önemle önerilir.  
  
 `pwszBuildFlavor`  
 'ndaki CLR 'nin sunucunun mi yoksa iş istasyonu derlemesinin mi yükleneceğini belirten bir dize. Geçerli değerler `svr` ve `wks`. Sunucu derlemesi, çöp koleksiyonları için birden fazla işlemciden yararlanmak üzere iyileştirilmiştir ve iş istasyonu derlemesi, tek işlemcili bir makinede çalışan istemci uygulamaları için iyileştirilmiştir.  
  
 `pwszBuildFlavor` null olarak ayarlandıysa, iş istasyonu derlemesi yüklenir. Tek işlemcili bir makinede çalışırken, `pwszBuildFlavor` `svr`olarak ayarlanmış olsa bile iş istasyonu derlemesi her zaman yüklenir. Ancak, `pwszBuildFlavor` `svr` olarak ayarlanırsa ve eşzamanlı çöp toplama belirtilirse (`flags` parametresinin açıklamasına bakın), sunucu derlemesi yüklenir.  
  
 `rclsid`  
 'ndaki [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass 'ın `CLSID`. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki İstenen arabirimin `rclsid``IID`. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı `riid`için döndürülen arabirim işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `pwszVersion` var olmayan bir çalışma zamanı sürümünü belirtiyorsa, `CorBindToRuntimeEx` bir HRESULT değeri döndürür.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Windows kimliğinin yürütme bağlamı ve akışı  
 CLR sürüm 1 ' de, <xref:System.Security.Principal.WindowsIdentity> nesnesi yeni iş parçacıkları, iş parçacığı havuzları veya zamanlayıcı geri çağırmaları gibi zaman uyumsuz noktalara akmaz. CLR sürüm 2,0 ' de, bir <xref:System.Threading.ExecutionContext> nesnesi şu anda yürütülmekte olan iş parçacığı hakkında bazı bilgileri sarmalanmış ve uygulama etki alanı sınırları boyunca değil, herhangi bir zaman uyumsuz noktada akar. Benzer şekilde, <xref:System.Security.Principal.WindowsIdentity> nesnesi de herhangi bir zaman uyumsuz noktada akar. Bu nedenle, iş parçacığında geçerli kimliğe bürünme, varsa, akış.  
  
 Akışı iki şekilde değiştirebilirsiniz:  
  
1. İş parçacığı temelinde akışı bastırmak için <xref:System.Threading.ExecutionContext> ayarlarını değiştirerek (<xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>ve <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> yöntemlerine bakın).  
  
2. İşlem varsayılan modunu sürüm 1 uyumluluk modu olarak değiştirerek, <xref:System.Security.Principal.WindowsIdentity> nesnenin geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> ayarlarından bağımsız olarak herhangi bir zaman uyumsuz noktada akış yapmaz. Varsayılan modu değiştirme, CLR 'yi yüklemek için yönetilen bir çalıştırılabiliri veya yönetilmeyen barındırma arabirimini kullanıp kullanmayacağınızı bağlıdır:  
  
    1. Yönetilen yürütülebilir dosyalar için [\<Legacyımpersonationpolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) öğesinin `enabled` özniteliğini `true`olarak ayarlamanız gerekir.  
  
    2. Yönetilmeyen barındırma arabirimleri için, `CorBindToRuntimeEx` işlevini çağırırken `flags` parametresindeki `STARTUP_LEGACY_IMPERSONATION` bayrağını ayarlayın.  
  
     Sürüm 1 uyumluluk modu tüm işlem ve işlemdeki tüm uygulama etki alanları için geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve `CorBindToRuntime` aynı işlemi gerçekleştirir, ancak `CorBindToRuntimeEx` IşLEVI, clr 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
