---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235954"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4. 5'altında serileştirilen MailMessage nesneleri seri durumdan çıkarma işlemi başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 ile başlayarak <xref:System.Web.Mail.MailMessage> nesneleri, ASCII olmayan karakterler içerebilir. .NET Framework 4'te yalnızca ASCII karakterleri desteklenir. <xref:System.Web.Mail.MailMessage> ASCII olmayan karakterler içeren ve .NET Framework 4.5 ya da daha sonra serileştirilmiş nesneler, .NET Framework 4 altında seri durumdan çıkarılamıyor.|
|Öneri|Kodunuzu işlenirken özel durum işleme sağladığı, bir <xref:System.Web.Mail.MailMessage> nesne.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
