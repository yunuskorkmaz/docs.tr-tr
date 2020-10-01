---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608060"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET hatalı çok parçalı işleme, form verilerinde kayıp oluşmasına neden olabilir.

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, ASP.NET çok parçalı sınır değerlerini yanlış ayrıştırarak, istek yürütme sırasında form verilerinin kullanılamamasına neden olabilirler. .NET Framework 4,8 veya sonraki sürümleri hedefleyen uygulamalar çok parçalı verileri doğru şekilde ayrıştırır, bu nedenle form değerleri istek yürütmesi sırasında kullanılabilir.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,8 üzerinde çalışan uygulamalarla başlayarak, öğesini kullanarak .NET Framework 4,8 veya üzeri bir sürümü hedeflerken <code>targetFrameworkVersion</code> , varsayılan davranış şerit sınırlayıcıları olarak değişir. Önceki Framework sürümlerini hedeflerken veya kullanmayan <code>targetFrameworkVersion</code> bazı değerler için sondaki sınırlayıcılar yine de döndürülür. Bu davranış, ayrıca bir ile açıkça denetlenebilir <code>appSetting</code> :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Bilinmiyor|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
