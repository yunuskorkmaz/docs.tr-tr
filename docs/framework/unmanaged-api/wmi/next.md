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
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726797"
---
# <a name="next-function"></a>Next işlevi

Bir [beginenumeration](beginenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki bir sonraki özelliği alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi

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
dışı `BSTR` Özellik adını içeren yeni bir. Ad gerekmiyorsa, bu parametreyi olarak ayarlayabilirsiniz `null` .

`pVal`\
dışı , `VARIANT` Özelliğinin değeri ile doldurulmuştur. Değer gerekmiyorsa, bu parametreyi olarak ayarlayabilirsiniz `null` . İşlev bir hata kodu döndürürse, `VARIANT` geçilen öğesine `pVal` değiştirilmemiş olarak kalır.

`pvtType`\
dışı Bir `CIMTYPE` değişken işaretçisi ( `LONG` özelliğin türünün yerleştirildiği bir). Bu özelliğin değeri bir olabilir `VT_NULL_VARIANT` , bu durumda özelliğin gerçek türünü belirlenmesi gerekir. Bu parametre de olabilir `null` .

`plFlavor`\
[out] `null` veya özelliğin kaynağına bilgi alan bir değer. Olası değerler için [açıklamalar] bölümüne bakın.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101D | İşleve bir çağrı yoktu [`BeginEnumeration`](beginenumeration.md) . |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile Windows Yönetimi arasındaki uzak yordam çağrısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada daha fazla özellik yok. |

## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) yöntemine bir çağrı kaydırır.

Bu yöntem ayrıca sistem özelliklerini de döndürür.

Özelliğin temeldeki türü bir nesne yolu, bir tarih veya saat ya da başka bir özel tür ise, döndürülen tür yeterli bilgi içermez. Çağıran, `CIMTYPE` özelliğin bir nesne başvurusu, bir tarih veya saat ya da başka bir özel tür olduğunu belirleyebilmek için belirtilen özelliği için öğesini incelemesi gerekir.

`plFlavor`Değilse `null` , `LONG` değeri özelliğin kaynağı hakkında aşağıdaki gibi bilgileri alır:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Özelliği, standart bir sistem özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: özellik üst sınıftan devralınır. <br> Bir örnek için: üst sınıftan Devralındığı sürece özelliği, örnek tarafından değiştirilmez.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: özellik türetilmiş sınıfa aittir. <br> Bir örnek için: özelliği örnek tarafından değiştirilir; diğer bir deyişle, bir değer sağlanmış veya bir niteleyici eklenmiş ya da değiştirilmiş. |

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
