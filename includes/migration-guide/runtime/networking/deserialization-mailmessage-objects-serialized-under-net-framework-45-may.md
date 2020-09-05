---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497122"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4,5 altında seri hale getirilen MailMessage nesnelerinin serisini kaldırma işlemi başarısız olabilir

#### <a name="details"></a>Ayrıntılar

4,5 .NET Framework başlayarak, <xref:System.Web.Mail.MailMessage> nesneler ASCII olmayan karakterler içerebilir. .NET Framework 4 ' te yalnızca ASCII karakterleri desteklenir. <xref:System.Web.Mail.MailMessage> ASCII olmayan karakterler içeren ve .NET Framework 4,5 veya üzeri bir sürümde seri hale getirilen nesneler .NET Framework 4 altında seri durumdan çıkarılamıyor.

#### <a name="suggestion"></a>Öneri

Bir nesne seri durumdan çıkarılırken kodunuzun özel durum işleme sağladığından emin olun <xref:System.Web.Mail.MailMessage> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
