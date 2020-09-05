---
ms.openlocfilehash: ed669364efe9dd8f57d831a3764dd3fc68cd5e05
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497609"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="cab55-101">ASP.NET hatalı çok parçalı işleme, form verilerinde kayıp oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cab55-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="cab55-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cab55-102">Details</span></span>

<span data-ttu-id="cab55-103">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, ASP.Net çok parçalı sınır değerlerini yanlış ayrıştırarak, istek yürütme sırasında form verilerinin kullanılamamasına neden olabilirler.</span><span class="sxs-lookup"><span data-stu-id="cab55-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="cab55-104">.NET Framework 4,8 veya sonraki sürümleri hedefleyen uygulamalar çok parçalı verileri doğru şekilde ayrıştırır, bu nedenle form değerleri istek yürütmesi sırasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cab55-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cab55-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="cab55-105">Suggestion</span></span>

<span data-ttu-id="cab55-106">.NET Framework 4,8 üzerinde çalışan uygulamalarla başlayarak, öğesini kullanarak .NET Framework 4,8 veya üzeri bir sürümü hedeflerken <code>targetFrameworkVersion</code> , varsayılan davranış şerit sınırlayıcıları olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="cab55-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="cab55-107">Önceki Framework sürümlerini hedeflerken veya kullanmayan <code>targetFrameworkVersion</code> bazı değerler için sondaki sınırlayıcılar yine de döndürülür. Bu davranış, ayrıca bir ile açıkça denetlenebilir <code>appSetting</code> :</span><span class="sxs-lookup"><span data-stu-id="cab55-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="cab55-108">Name</span><span class="sxs-lookup"><span data-stu-id="cab55-108">Name</span></span>    | <span data-ttu-id="cab55-109">Değer</span><span class="sxs-lookup"><span data-stu-id="cab55-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cab55-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="cab55-110">Scope</span></span>   |<span data-ttu-id="cab55-111">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="cab55-111">Unknown</span></span>|
|<span data-ttu-id="cab55-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="cab55-112">Version</span></span>|<span data-ttu-id="cab55-113">4,8</span><span class="sxs-lookup"><span data-stu-id="cab55-113">4.8</span></span>|
|<span data-ttu-id="cab55-114">Tür</span><span class="sxs-lookup"><span data-stu-id="cab55-114">Type</span></span>|<span data-ttu-id="cab55-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="cab55-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cab55-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cab55-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
