---
title: Next işlevi (yönetilmeyen API Başvurusu)
description: Next işlevi bir Numaralandırmadaki sonraki özelliği alır.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127372"
---
# <a name="next-function"></a>Next işlevi
Bir [beginenumeration](beginenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki bir sonraki özelliği alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lFlags`\
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pstrName`\
dışı Özellik adını içeren yeni bir `BSTR`. Ad gerekli değilse bu parametreyi `null` olarak ayarlayabilirsiniz.

`pVal`\
dışı Özelliğin değeriyle doldurulmuş bir `VARIANT`. Değer gerekli değilse bu parametreyi `null` olarak ayarlayabilirsiniz. İşlev bir hata kodu döndürürse, `pVal` geçirilen `VARIANT` değiştirilmemiş olarak kalır.

`pvtType`\
dışı `CIMTYPE` değişkenine yönelik bir işaretçi (özelliğin türünün yerleştirildiği bir `LONG`). Bu özelliğin değeri bir `VT_NULL_VARIANT`olabilir, bu durumda özelliğin gerçek türünü belirlemesi gerekir. Bu parametre de `null`olabilir.

`plFlavor`\
[out] `null`veya özelliğin kaynağına bilgi alan bir değer. Olası değerler için [açıklamalar] bölümüne bakın.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101D | [`BeginEnumeration`](beginenumeration.md) işlevine hiçbir çağrı yoktu. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile Windows Yönetimi arasındaki uzak yordam çağrısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada daha fazla özellik yok. |

## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) yöntemine bir çağrı kaydırır.

Bu yöntem ayrıca sistem özelliklerini de döndürür.

Özelliğin temeldeki türü bir nesne yolu, bir tarih veya saat ya da başka bir özel tür ise, döndürülen tür yeterli bilgi içermez. Çağıran, özelliğin bir nesne başvurusu, bir tarih veya saat ya da başka bir özel tür olup olmadığını belirlemesi için belirtilen özelliğin `CIMTYPE` incelemesi gerekir.

`plFlavor` `null`değilse, `LONG` değeri özelliğin kaynağı hakkında aşağıdaki gibi bilgileri alır:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Özelliği, standart bir sistem özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: özellik üst sınıftan devralınır. <br> Bir örnek için: üst sınıftan Devralındığı sürece özelliği, örnek tarafından değiştirilmez.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: özellik türetilmiş sınıfa aittir. <br> Bir örnek için: özelliği örnek tarafından değiştirilir; diğer bir deyişle, bir değer sağlanmış veya bir niteleyici eklenmiş ya da değiştirilmiş. |

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
