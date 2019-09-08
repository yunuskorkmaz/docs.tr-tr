---
title: CompareTo işlevi (yönetilmeyen API Başvurusu)
description: CompareTo işlevi bir nesneyi başka bir WMI nesnesiyle karşılaştırır.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798777"
---
# <a name="compareto-function"></a>CompareTo işlevi

Bir nesneyi başka bir Windows Yönetim nesnesiyle karşılaştırır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`flags`\
'ndaki Karşılaştırma için göz önünde bulundurmanız gereken nesne özelliklerini belirten bayrakların bit düzeyinde birleşimi. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

`pCompareTo`\
'ndaki Karşılaştırılacak nesne. `pCompareTo`geçerli bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği olmalıdır; Bu, `null`olamaz.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101D | İçin bir araya giren `BeginEnumeration` [`EndEnumeration`](endenumeration.md)çağrı yapılmadan ikinci bir çağrı yapıldı. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Nesneler farklı. |
| `WBEM_S_SAME` | 0 | Nesneler, karşılaştırma bayraklarına göre aynıdır. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) yöntemine bir çağrı kaydırır.

`lEnumFlags` Bağımsız değişken olarak geçirilebilecek bayraklar, *wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz. Aşağıdaki bayrakların bit düzeyinde birleşimini belirterek, karşılaştırmaya dahil olan tek tek özellikleri belirtebilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Kaynağı (sunucu ve geldiği ad alanı) yok sayın. |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1\. | Tüm niteleyicileri yoksay ( **anahtar** ve **dinamik**dahil) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Özelliklerin varsayılan değerlerini yoksayın. Bu bayrak yalnızca sınıfların karşılaştırılması için geçerlidir. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Niteleyici niteleyicisini yoksayın. Bu bayrak hala niteleyicileri hesaba ayırır, ancak yayma kuralları ve geçersiz kılma kısıtlamaları gibi özellik ayrımlarını yoksayar. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Dize değerlerini karşılaştıran büyük/küçük harf durumunu yoksayın. Bu, hem dizeler hem de niteleyici değerleri için geçerlidir. Özellik ve niteleyici adlarının karşılaştırılması, bu bayrağın ayarlanmış olup olmamasına bakılmaksızın her zaman büyük/küçük harfe duyarlıdır. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Karşılaştırılan nesnelerin aynı sınıfın örnekleri olduğunu varsayın. Sonuç olarak, bu bayrak yalnızca örnekle ilgili bilgileri karşılaştırır. Performansı iyileştirmek için bu bayrakları kullanın. Nesneler aynı sınıftan değilse, sonuçlar tanımsızdır. |

Ya da şu şekilde tek bir bileşik bayrak belirtebilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Karşılaştırmayla tüm özellikleri göz önünde bulundurun. |

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
