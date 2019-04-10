---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235799"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>UTF7 HttpRequest.ContentEncoding özelliği engeller

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5 ' başlayarak, UTF-7 kodlaması MMC'deki <xref:System.Web.HttpRequest?displayProperty=name>s' gövdesi. Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.|
|Öneri|İdeal olarak, uygulamalar UTF-7 içinde kodlama kullanmayacak şekilde güncelleştirilmelidir <xref:System.Web.HttpRequest?displayProperty=name>s. Alternatif olarak, eski davranışı kullanılarak geri yüklenebilir <code>aspnet:AllowUtf7RequestContentEncoding</code> özniteliği [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) öğesi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
