---
title: QuotedPairReader sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990372"
---
# <a name="quotedpairreader-class"></a>QuotedPairReader sınıfı

Tırnak işaretli bir dizede hangi karakterlerin alıntılanmış (kaçışlı) olduğunu belirler. Bu sınıf devralınamaz.

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="countquotedchars-method"></a>CountQuotedChars yöntemi

Belirtilen dizedeki, önceki tırnak içine alınmış birden fazla ters eğik çizgi dahil olmak üzere ardışık olarak tırnak içine alınmış karakterlerin sayısını sayar Örneğin, dize `a\\\b` ve bir dizini verildiğinde, tırnak işareti `4` `4` `b` alınır ve bu nedenle önceki üç ters eğik çizgi bulunur.

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>Parametreler

- `data` <xref:System.String>

  Ardışık alıntılanmış karakterlerin sayımının bulunduğu veri dizesi.

- `index` <xref:System.Int32>

  Belirtilen dizedeki, ardışık olarak hangi tırnak işaretli karakterlerin sayılmaması gereken konum.

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`Unicode karakterlerinin atlanmasına izin vermek için; Aksi takdirde, `false` .

### <a name="return-value"></a>Döndürülen değer

<xref:System.Int32?displayProperty=nameWithType>

`0`Belirtilen dizindeki karakter kaçışsız ise; Aksi takdirde, ardışık olarak karakter dahil olmak üzere karakteri de içerecek şekilde ardışık tırnak işareti sayısı `index` .

### <a name="exceptions"></a>Özel durumlar

<xref:System.FormatException?displayProperty=nameWithType>

Atlanan bir Unicode karakteri bulundu, ancak buna izin verilmiyor.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
