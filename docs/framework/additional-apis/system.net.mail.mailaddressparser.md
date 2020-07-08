---
title: MailAddressParser sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051356"
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
