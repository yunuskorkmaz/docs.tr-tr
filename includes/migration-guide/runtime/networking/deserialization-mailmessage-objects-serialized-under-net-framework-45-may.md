---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620639"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4,5 altında seri hale getirilen MailMessage nesnelerinin serisini kaldırma işlemi başarısız olabilir

#### <a name="details"></a>Ayrıntılar

4,5 .NET Framework başlayarak, <xref:System.Web.Mail.MailMessage> nesneler ASCII olmayan karakterler içerebilir. .NET Framework 4 ' te yalnızca ASCII karakterleri desteklenir. <xref:System.Web.Mail.MailMessage>ASCII olmayan karakterler içeren ve .NET Framework 4,5 veya üzeri bir sürümde seri hale getirilen nesneler .NET Framework 4 altında seri durumdan çıkarılamıyor.

#### <a name="suggestion"></a>Öneri

Bir nesne seri durumdan çıkarılırken kodunuzun özel durum işleme sağladığından emin olun <xref:System.Web.Mail.MailMessage> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
