---
ms.openlocfilehash: 26facb645de175d7ef0432394fc2b84f59e8437d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496811"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>MaxRequestLength veya maxReceivedMessageSize için hata kodları farklı

#### <a name="details"></a>Ayrıntılar

Internet Information Services (IIS) veya ASP.NET geliştirme sunucusunda barındırılan, maxRequestLength (ASP.NET) veya maxReceivedMessageSize (WCF 'de) ' da bulunan WCF Web hizmetlerindeki iletiler, HTTP durum kodu 400 (Hatalı Istek) ile 413 (Istek varlığı çok büyük) olarak değiştirilmiştir ve maxRequestLength veya maxReceivedMessageSize ayarını aşan iletiler bir <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> özel durum oluşturur. Bu, aktarım modunun akışa alındığı durumları içerir.

#### <a name="suggestion"></a>Öneri

Bu değişiklik, ileti uzunluğunun ASP.NET veya WCF tarafından izin verilen sınırları aştığı durumlarda hata ayıklamayı kolaylaştırır. HTTP 400 durum koduna göre işlem yapan tüm kodları değiştirmeniz gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
