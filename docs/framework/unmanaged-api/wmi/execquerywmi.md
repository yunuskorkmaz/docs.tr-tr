---
title: ExecQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecQueryWmi işlevi, nesneleri almak için bir sorgu yürütür.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130428"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi işlevi

Nesneleri almak için bir sorgu yürütür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Parametreler

`strQueryLanguage`\
'ndaki Windows yönetimi tarafından desteklenen geçerli sorgu diline sahip bir dize. WMI Sorgu Dili için kısaltmasının "WQL" olması gerekir.

`strQuery`\
'ndaki Sorgunun metni. Bu parametre `null`olamaz.

`lFlags`\
'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

| Sabit | Değer  | Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlanırsa, işlev geçerli bağlantının yerel ayarında yerelleştirilmiş ad alanında depolanan değiştirilmiş niteleyicileri alır. <br/> Ayarlanmamışsa, işlev yalnızca anında ad alanında depolanan niteleyicileri alır. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrak, yarı zaman uyumlu bir çağrıya neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev, salt ileri bir Numaralandırıcı döndürür. Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez. |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI, serbest bırakılana kadar Numaralandırmadaki nesnelere işaretçiler tutar. |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Döndürülen tüm nesnelerin, **__Path**, **__Relpath**ve **__server**gibi sistem özelliklerinin `null`olmamasını sağlar. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Bu bayrak prototipleme için kullanılır. Sorguyu yürütmez ve bunun yerine tipik bir sonuç nesnesi gibi görünen bir nesne döndürür. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | , Kendi üst sınıfı veya alt sınıflarından bağımsız kalmadan belirtilen sınıf için sağlayıcıya doğrudan erişim sağlar. |

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve en iyi performans için `WBEM_FLAG_FORWARD_ONLY`.

`pCtx`\
'ndaki Genellikle, bu değer `null`. Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.

`ppEnum`\
dışı Herhangi bir hata oluşursa, çağıranın sorgunun sonuç kümesindeki örnekleri almasına izin veren Numaralandırıcı için işaretçiyi alır. Sorgu sıfır örnek içeren bir sonuç kümesine sahip olabilir. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

`authLevel`\
'ndaki Yetkilendirme düzeyi.

`impLevel`\
'ndaki Kimliğe bürünme düzeyi.

`pCurrentNamespace`\
'ndaki Geçerli ad alanını temsil eden bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.

`strUser`\
'ndaki Kullanıcı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`strPassword`\
'ndaki Parola. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`strAuthority`\
'ndaki Kullanıcının etki alanı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının işlevin döndüregörüntüleyebileceği bir veya daha fazla sınıfı görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Sorguda sözdizimi hatası vardı. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | İstenen sorgu dili desteklenmiyor. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Sorgu çok karmaşık. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor. [Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Sorgu var olmayan bir sınıfı belirtiyor. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemServices:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) yöntemine bir çağrı kaydırır.

Bu işlev `strQuery` parametresinde belirtilen sorguyu işler ve çağıranın sorgu sonuçlarına erişebileceği bir Numaralandırıcı oluşturur. Numaralandırıcı bir [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) arabirimine yönelik bir işaretçidir; sorgu sonuçları, [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) arabirimi aracılığıyla kullanılabilir hale getirilen sınıf nesnelerinin örnekleridir.

WQL sorgularında kullanılabilecek `AND` sayısı ve `OR` anahtar kelimeleriyle ilgili sınırlar vardır. Karmaşık bir sorguda kullanılan çok sayıda WQL anahtar sözcüğü, WMI 'nin `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu `HRESULT` değeri olarak döndürmesini sağlayabilir. WQL anahtar kelimesinin sınırı, sorgunun ne kadar karmaşık olduğuna bağlıdır.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
