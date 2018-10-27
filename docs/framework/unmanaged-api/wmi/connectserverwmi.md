---
title: ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)
description: ConnectServerWmi işlev bir WMI ad alanı için bir bağlantı oluşturmak için DCOM kullanır.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa4b789641034b6563b15c52e96cbfdfa13d989a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049288"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi işlevi
Belirtilen bir bilgisayardaki bir WMI ad alanına DCOM aracılığıyla yapılan bağlantı oluşturur.  
  
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

`strNetworkResource` [in] Geçerli bir işaretçi `BSTR` , doğru WMI ad alanının nesne yolu içerir. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.

`strUser` [in] Geçerli bir işaretçi `BSTR` , kullanıcı adını içerir. A `null` değeri, geçerli güvenlik bağlamı gösterir. Kullanıcı geçerli olandan farklı bir etki alanından ise `strUser` ters eğik çizgiyle bölünerek etki alanı ve kullanıcı adı da içerebilir. `strUser` Ayrıca kullanıcı asıl adı (UPN) biçiminde gibi olabilir `userName@domainName`. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.

`strPassword` [in] Geçerli bir işaretçi `BSTR` , parola içeriyor. A `null` geçerli güvenlik bağlamı gösterir. Boş bir dize ("") geçerli sıfır uzunlukta bir parola belirtir.

`strLocale` [in] Geçerli bir işaretçi `BSTR` bilgi almak için doğru yerel gösterir. Microsoft yerel ayar tanımlayıcılarını için dize biçimindedir "MS\_*xxx*" burada *xxx* yerel ayar tanıtıcısı (LCID) gösteren onaltılık biçimde bir dizedir. Geçersiz bir yerel ayar belirtilmezse yöntem döndürür `WBEM_E_INVALID_PARAMETER` hariç Windows 7 varsayılan yerel ayar sunucusunun kullanıldığı bunun yerine,. Varsa ' null1, geçerli yerel ayarı kullanılır. 
 
`lSecurityFlags` [in] Geçirilecek bayrakları `ConnectServerWmi` yöntemi. Bu parametre için sıfır (0) değerini sonuçları çağrısında `ConnectServerWmi` yalnızca bir sunucu bağlantısı kurulduktan sonra döndürüyor. Bu uygulamada süresiz olarak sunucunun bozuk olup olmadığını yanıt vermiyorsa sonuçlanabilir. Geçerli bir değerler şunlardır:

| Sabit  | Değer  | Açıklama  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | İç kullanım için ayrılmıştır. Kullanmayın. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` iki dakika içinde ya da daha az döndürür. |

`strAuthority` [in] Kullanıcı etki alanı adı. Aşağıdaki değerlere sahip olabilir:

| Değer | Açıklama |
|---------|---------|
| Boş | NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır. Varsa `strUser` belirtir (önerilen konum) buraya belirtilmemelidir. İşlev döndürür `WBEM_E_INVALID_PARAMETER` iki parametrede de etki alanı belirtirseniz. |
| Kerberos:*asıl adı* | Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir. |
| NTLMDOMAIN:*etki alanı adı* | NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adı içerir. |

`pCtx`   
[in] Genellikle, bu parametre `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) nesnesi bir veya daha fazla dinamik sınıfı sağlayıcıları tarafından gerekiyor. 

`ppNamespace`  
[out] İşlevi döndüğünde, bir işaretçi alır bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesne belirtilen ad alanına bağlı. İşaret edecek şekilde ayarlanmış `null` bir hata olduğunda.

`impLevel`  
[in] Kimliğe bürünme düzeyi.

`authLevel`  
[in] Yetkilendirme düzeyi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) yöntemi.

 Yerel erişim için varsayılan ad alanı `strNetworkResource` basit nesne yolu olabilir: "kök\varsayılan" veya "\\.\root\default". Uzak bir bilgisayarda varsayılan ad alanı erişimi için COM veya Microsoft ile uyumlu ağ kullanarak dahil bilgisayar adı: "\\myserver\root\default". Bilgisayar adı, ayrıca bir DNS adı veya IP adresi olabilir. `ConnectServerWmi` İşlevi IPv6 çalıştıran bilgisayarlarla da bağlanabilir bir IPv6 adresi kullanarak.

`strUser` Boş bir dize olamaz. Etki alanı belirtilirse `strAuthority`, bu da de dahil edilmemesi gerekir `strUser`, ya da bir işlev döndürür `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
