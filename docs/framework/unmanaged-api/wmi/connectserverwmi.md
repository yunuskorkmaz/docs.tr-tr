---
title: ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)
description: ConnectServerWmi işlevi, bir WMI ad alanına bağlantı oluşturmak için DCOM kullanır.
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
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798745"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi işlevi

Belirtilen bir bilgisayardaki WMI ad alanına DCOM aracılığıyla bir bağlantı oluşturur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
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

`strNetworkResource`\
'ndaki Doğru WMI ad alanının `BSTR` nesne yolunu içeren geçerli bir işaretçi. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

`strUser`\
'ndaki Kullanıcı adını içeren geçerli `BSTR` bir işaretçisi. Bir `null` değer geçerli güvenlik bağlamını gösterir. Kullanıcı geçerli olandan farklı bir etki alanından farklıysa, `strUser` bir ters eğik çizgiyle ayrılmış etki alanını ve Kullanıcı adını da içerebilir. `strUser`, gibi Kullanıcı asıl adı (UPN) biçiminde de olabilir `userName@domainName`. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

`strPassword`\
'ndaki Parolayı içeren geçerli `BSTR` bir işaretçisi. Geçerli güvenlik bağlamını gösterir. `null` Boş bir dize ("") geçerli bir sıfır uzunlukta parolayı gösterir.

`strLocale`\
'ndaki Bilgi alımı için doğru yerel `BSTR` ayarı gösteren geçerli bir işaretçisi. Microsoft yerel ayar tanımlayıcıları için, dizenin biçimi "MS\_*XXX*", burada *XXX* , yerel ayar tanımlayıcısını (LCID) gösteren onaltılık biçimli bir dizedir. Geçersiz bir yerel ayar belirtilmişse, yöntem bunun yerine sunucunun `WBEM_E_INVALID_PARAMETER` varsayılan yerel ayarının kullanıldığı Windows 7 hariç döndürülür. Eğer ' null1, geçerli yerel ayar kullanılır.

`lSecurityFlags`\
'ndaki `ConnectServerWmi` Yönteme geçirilecek bayraklar. Bu parametre için sıfır (0) değeri, yalnızca sunucuya bağlantı kurulduktan sonra `ConnectServerWmi` döndürme çağrısına neden olur. Bu, sunucu bozulur bir uygulamanın süresiz olarak yanıt vermemesine neden olabilir. Diğer geçerli değerler şunlardır:

| Sabit  | Değer  | Açıklama  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Dahili kullanım için ayrılmıştır. Kullanmayın. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`iki dakika veya daha kısa bir süre döndürür. |

`strAuthority`\
'ndaki Kullanıcının etki alanı adı. Aşağıdaki değerlere sahip olabilir:

| Değer | Açıklama |
|---------|---------|
| adet | NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır. Etki alanını (önerilen konum) belirtiyorsa,buradabelirtilmemelidir.`strUser` İşlevi, etki `WBEM_E_INVALID_PARAMETER` alanını her iki parametrede de belirtirseniz döndürür. |
| Kerberos:*asıl ad* | Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir. |
| NTLMDOMAIN:*etki alanı adı* | NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adı içerir. |

`pCtx`\
'ndaki Genellikle, bu parametre `null`. Aksi takdirde, bir veya daha fazla dinamik sınıf sağlayıcısı için gereken bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) nesnesine yönelik bir işaretçidir.

`ppNamespace`\
dışı İşlev döndüğünde, belirtilen ad alanına göre bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine bir işaretçi alır. Bir hata olduğunda ' ı işaret `null` etmek üzere ayarlanır.

`impLevel`\
'ndaki Kimliğe bürünme düzeyi.

`authLevel`\
'ndaki Yetkilendirme düzeyi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) yöntemine bir çağrı kaydırır.

Varsayılan ad alanına `strNetworkResource` yerel erişim için basit bir nesne yolu olabilir: "root\default" veya "\\.\root\default". COM veya Microsoft uyumlu ağ kullanarak uzak bir bilgisayardaki varsayılan ad alanına erişim için, bilgisayar adı: "\\myserver\root\default" ifadesini ekleyin. Bilgisayar adı da bir DNS adı veya IP adresi olabilir. `ConnectServerWmi` İşlevi IPv6 adresini kullanarak IPv6 çalıştıran bilgisayarlarla da bağlanabilir.

`strUser`boş bir dize olamaz. Etki alanı içinde `strAuthority`belirtilmişse, ' de `strUser`dahil edilmemelidir ya da işlev döndürülür `WBEM_E_INVALID_PARAMETER`.

## <a name="requirements"></a>Gereksinimler

 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi** WMINet_Utils. IDL

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
