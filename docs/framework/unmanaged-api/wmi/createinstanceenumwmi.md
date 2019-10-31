---
title: Createınstanceenumwmi işlevi (yönetilmeyen API Başvurusu)
description: Createınstanceenumwmi işlevi, seçim ölçütlerine uyan belirli bir sınıfın örneklerini içeren bir Numaralandırıcı döndürür.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9ffa718be0e8b67471fdf8cb277df201388d2840
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130410"
---
# <a name="createinstanceenumwmi-function"></a>Createınstanceenumwmi işlevi

Belirtilen seçim ölçütlerine uyan belirli bir sınıfın örneklerini döndüren bir Numaralandırıcı döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
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

`strFilter`\
'ndaki Örnekleri istenen sınıfın adı. Bu parametre `null`olamaz.

`lFlags`\
'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlanırsa, işlev geçerli bağlantının yerel ayarında yerelleştirilmiş ad alanında depolanan değiştirilmiş niteleyicileri alır. <br/> Ayarlanmamışsa, işlev yalnızca anında ad alanında depolanan niteleyicileri alır. |
| `WBEM_FLAG_DEEP` | 0 | Sabit listesi bu ve hiyerarşideki tüm alt sınıfları içerir. |
| `WBEM_FLAG_SHALLOW` | 1\. | Sabit listesi yalnızca bu sınıfın saf örneklerini içerir ve bu sınıfta bulunmayan özellikleri sağlayan tüm alt sınıfların örneklerini dışlar. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrak, yarı zaman uyumlu bir çağrıya neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev, salt ileri bir Numaralandırıcı döndürür. Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez. |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI, serbest bırakılana kadar Numaralandırmadaki nesnelere işaretçiler tutar. |

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve en iyi performans için `WBEM_FLAG_FORWARD_ONLY`.

`pCtx`\
'ndaki Genellikle, bu değer `null`. Aksi takdirde, istenen örnekleri sağlayan sağlayıcı tarafından kullanılabilecek bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.

`ppEnum`\
dışı Numaralandırıcı için işaretçiyi alır.

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının belirtilen sınıfın örneklerini görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter` yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor. [Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) yöntemi çağrısını sarmalanmış.

Döndürülen Numaralandırıcı sıfır öğelerine sahip olabileceğini unutmayın.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
