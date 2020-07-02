---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620652"
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
