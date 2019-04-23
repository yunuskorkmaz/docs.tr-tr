---
ms.openlocfilehash: e6b0387d9d04aa979de289ea0c5caa6c76f4d1be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982273"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET yanlış çok bölümlü işleme kayıp form veri kaybına neden olabilir.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, ASP.Net yanlış çok bölümlü sınır değerleri, form verilerinde isteğin yürütülmesi sırasında kullanılamaz durumda olmasından kaynaklanan ayrıştırma. Form değerlerini istek yürütme sırasında kullanılabilir olmaması doğru .NET Framework 4.8 veya sonraki sürümlerini hedefleyen uygulamalar çok parçalı verileri ayrıştırılamıyor.|
|Öneri|.NET Framework 4.8 hedeflenirken veya kullanarak daha sonra .NET Framework 4.8 üzerinde çalışan uygulamalar ile başlayan <code>targetFrameworkVersion</code> öğesinde, Şerit sınırlayıcılar için varsayılan davranış değişiklikleri. Zaman önceki framework sürümlerini hedefleme veya kullanmayan <code>targetFrameworkVersion</code>, yine de bazı değerler döndürülen için eklenen sınırlayıcılara. Bu davranış da açıkça ile denetlenebilir bir <code>appSetting</code>:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
