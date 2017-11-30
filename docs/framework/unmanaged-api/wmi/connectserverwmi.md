---
title: "ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)"
description: "ConnectServerWmi işlevi bir WMI ad alanı için bir bağlantı oluşturmak için DCOM kullanır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51050bce4603ebcfe99fb38d66e54683c677293
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi işlevi
Belirtilen bir bilgisayardaki bir WMI ad alanı için DCOM aracılığıyla yapılan bağlantı oluşturur.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a>Parametreler

`strNetworkResource`[in] Geçerli bir işaretçi `BSTR` doğru WMI ad alanının nesne yolu içerir. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.

`strUser`[in] Geçerli bir işaretçi `BSTR` kullanıcı adını içerir. A `null` değeri geçerli güvenlik bağlamı gösterir. Kullanıcı mevcut olandan farklı bir etki alanından ise `strUser` ters eğik çizgi ile ayrılmış etki alanı ve kullanıcı adı da içerebilir. `strUser`Ayrıca olması kullanıcı asıl adı (UPN) biçimlendirebilir, suhc olarak  *userName@domainName* . Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.

`strPassword`[in] Geçerli bir işaretçi `BSTR` parola içeriyor. A `null` geçerli güvenlik bağlamı gösterir. Boş bir dize ("") geçerli sıfır uzunlukta bir parola belirtir.

`strLocale`[in] Geçerli bir işaretçi `BSTR` bilgileri alma doğru yerel gösterir. Microsoft yerel ayar tanımlayıcılarını için dizesinin biçimi olan "MS\_*xxx*", burada *xxx* yerel ayar kimliği (LCID) gösteren onaltılık biçimde bir dizedir. Bu yöntem geçersiz bir yerel belirtilmiş olup olmadığını döndürür `WBEM_E_INVALID_PARAMETER` dışındaki Windows 7 sunucusunun varsayılan yerel ayar kullanıldığı bunun yerine,. Varsa ' null1, geçerli yerel ayar kullanılır. 
 
`lSecurityFlags`[in] Geçirilecek bayrakları `ConnectServerWmi` yöntemi. Bu parametre için sıfır (0) değeri sonuçları çağrısında `ConnectServerWmi` yalnızca bir sunucu bağlantısı kurulduktan sonra döndürüyor. Bu süresiz olarak sunucunun bozuk olup olmadığını yanıt vermeyen bir uygulamada neden olabilir. Diğer geçerli değerler şunlardır:

| Sabit  | Değer  | Açıklama  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | İç kullanım için ayrılmıştır. Kullanmayın. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`iki dakika veya daha az döndürür. |

`strAuthority`[in] Kullanıcının etki alanı adı. Aşağıdaki değerlere sahip olabilir:

| Değer | Açıklama |
|---------|---------|
| Boş | NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır. Varsa `strUser` (önerilen konum) etki alanını belirtir burada belirtilmemelidir. İşlevi döndürür `WBEM_E_INVALID_PARAMETER` parametrelerinin her ikisini de etki alanı belirtirseniz. |
| Kerberos:*asıl adı* | Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir. |
| NTLMDOMAIN:*etki alanı adı* | NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adını içerir. |

`pCtx`   
[in] Genellikle, bu parametre olan `null`. Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) bir veya daha fazla dinamik sınıf sağlayıcıları tarafından gerekli nesne. 

`ppNamespace`  
[out] İşlevi döndüğünde gösteren bir işaretçi alan bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) nesnesi belirtilen ad alanına bağlı. İşaret edecek şekilde ayarlanmış `null` hata olduğunda.

`impLevel`  
[in] Kimliğe bürünme düzeyi.

`authLevel`  
[in] Kimlik doğrulama düzeyi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) yöntemi.

 Varsayılan ad alanı yerel erişimi için `strNetworkResource` basit bir nesne yolu: "kök\varsayılan" veya "\\.\root\default". İçin uzak bir bilgisayarda varsayılan ad alanına erişimi COM veya Microsoft uyumlu ağ kullanarak içerecek bilgisayar adı: "\\myserver\root\default". Bilgisayar adı, ayrıca bir DNS adı veya IP adresi olabilir. `ConnectServerWmi` İşlevi IPv6 çalıştıran bilgisayarlarla da bağlanabileceği bir IPv6 adresi kullanarak.

`strUser`boş bir dize olamaz. Etki alanında belirtilmişse, `strAuthority`, ayrıca dahil gerekir değil `strUser`, veya işlevi döndürür `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
