---
ms.openlocfilehash: e6b0387d9d04aa979de289ea0c5caa6c76f4d1be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802594"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET Yanlış çok parçalı işleme, form verilerinin kaybolmasına neden olabilir.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, ASP.Net çok parçalı sınır değerlerini yanlış ayrıştırarak form verilerinin istek yürütme sırasında kullanılamamasına neden olabilir. .NET Framework 4.8 veya daha sonraki sürümleri hedefleyen uygulamalar çok parçalı verileri doğru bir şekilde ayrıştırın, böylece istek yürütme sırasında form değerleri kullanılabilir.|
|Öneri|.NET Framework 4.8 üzerinde çalışan uygulamalardan başlayarak,.NET Framework 4.8 <code>targetFrameworkVersion</code> veya daha sonra öğeyi kullanarak hedeflediğinizde, varsayılan davranış sınır layıcıları şeritlemek için değişir. Önceki çerçeve sürümlerini hedeflediğinizde veya kullanılmazken, <code>targetFrameworkVersion</code>bazı değerler için sınırlayıcıları takip eden ler yine de döndürülür. Bu davranış aynı zamanda açıkça <code>appSetting</code>bir ile kontrol edilebilir:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
