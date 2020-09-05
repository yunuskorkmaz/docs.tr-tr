---
ms.openlocfilehash: cf34c5df1badcfd86d8a07bafdf1b759234712e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496200"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest. Contentenkodlama özelliği yasaklar UTF7

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak UTF-7 kodlaması <xref:System.Web.HttpRequest?displayProperty=fullName> s ' gövdelerinde kullanılamaz. Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.

#### <a name="suggestion"></a>Öneri

İdeal olarak, uygulamaların s 'de UTF-7 kodlaması kullanmamalıdır <xref:System.Web.HttpRequest?displayProperty=fullName> . Alternatif olarak, eski davranış <code>aspnet:AllowUtf7RequestContentEncoding</code> [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) öğesinin özniteliği kullanılarak geri yüklenebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.ContentEncoding`

-->
