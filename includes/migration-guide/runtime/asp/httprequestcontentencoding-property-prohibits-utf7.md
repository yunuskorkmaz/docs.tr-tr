---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620531"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
