---
title: ExecNotificationQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecNotificationQueryWmi işlevi, olayları almak için bir sorgu yürütür.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3d8a7683eef52a5e91bf7aa84d5aa7db7dbdac8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130447"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi işlevi

Olayları almak için bir sorgu yürütür. Çağrı hemen döndürülür ve çağıran, gelen olaylar için döndürülen numaralandırıcıyı yoklayabilirler. Döndürülen Numaralandırıcı serbest bırakıldığında sorgu iptal edilir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ExecNotificationQueryWmi (
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
'ndaki Bu işlevin davranışını etkileyen aşağıdaki iki bayrakların birleşimi. Bu değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.

| Sabit | Değer  | Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrak, yarı zaman uyumlu bir çağrıya neden olur. Bu bayrak ayarlanmamışsa, çağrı başarısız olur. Bunun nedeni, olayların sürekli olarak alınması anlamına gelir, yani Kullanıcı Döndürülen numaralandırıcısı yoklamalıdır. Bu çağrıyı süresiz olarak engellemek olanaksız hale getirir. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev, salt ileri bir Numaralandırıcı döndürür. Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez. |

`pCtx`\
'ndaki Genellikle, bu değer `null`. Aksi takdirde, istenen olayları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.

`ppEnum`\
dışı Herhangi bir hata oluşursa, çağıranın sorgunun sonuç kümesindeki örnekleri almasına izin veren Numaralandırıcı için işaretçiyi alır. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

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
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Sorgu var olmayan bir sınıfı belirtiyor. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Olayların tesliminde çok fazla duyarlılık istendi. Daha büyük bir yoklama toleransı belirtilmelidir. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Sorgu Windows yönetiminin sağlayabileceğinden daha fazla bilgi ister. Bu `HRESULT`, bir olay sorgusu bir ad alanındaki tüm nesneleri yoklamaya yönelik bir istek ile sonuçlanırsa döndürülür. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Sorguda sözdizimi hatası vardı. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | İstenen sorgu dili desteklenmiyor. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Sorgu çok karmaşık. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor. [Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Sorgu ayrıştırılamıyor. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) yöntemine bir çağrı kaydırır.

İşlev çağrıldıktan sonra, çağıran `ppEnum` nesnesini bir [sonraki](next.md) işleve düzenli olarak geçirir ve kullanılabilir herhangi bir olay olup olmadığını görür.

WQL sorgularında kullanılabilecek `AND` sayısı ve `OR` anahtar kelimeleriyle ilgili sınırlar vardır. Karmaşık bir sorguda kullanılan çok sayıda WQL anahtar sözcüğü, WMI 'nin `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu `HRESULT` değeri olarak döndürmesini sağlayabilir. WQL anahtar kelimesinin sınırı, sorgunun ne kadar karmaşık olduğuna bağlıdır.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
