---
title: MailAddressParser sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990421"
---
# <a name="mailaddressparser-class"></a>MailAddressParser sınıfı

RFC 2822 ' de açıklandığı gibi e-posta adreslerini ayrıştırır. Bu sınıf devralınamaz.

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="parseaddress-method"></a>ParseAddress yöntemi

Belirtilen dizeden tek bir e-posta adresini ayrıştırır.

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>Parametreler

`data` <xref:System.String>

Ayrıştırılacak bir e-posta adresi içeren dize.

### <a name="return-value"></a>Döndürülen değer

<xref:System.Net.Mail.MailAddress>

Geçerli bir e-posta adresi.

### <a name="exceptions"></a>Özel durumlar

<xref:System.FormatException?displayProperty=nameWithType>

E-posta adresi geçersiz.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
