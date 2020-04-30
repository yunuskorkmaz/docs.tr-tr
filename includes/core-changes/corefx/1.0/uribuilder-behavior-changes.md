---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595694"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="e8d8c-101">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="e8d8c-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="e8d8c-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType>Artık önde gelen `#` bir karakter önüne alınmaz ve <xref:System.UriBuilder.Query?displayProperty=nameWithType> bir tane zaten varsa öndeki `?` bir karakter artık yer almıyor.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e8d8c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e8d8c-103">Change description</span></span>

<span data-ttu-id="e8d8c-104">.NET Framework ' de, <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> ve <xref:System.UriBuilder.Query?displayProperty=nameWithType> özellikleri sırasıyla, depolanan değere `#` göre `?` veya karakter başına her zaman eklenir.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="e8d8c-105">Bu davranış, dize zaten bu `#` önde `?` gelen karakterlerden birini içeriyorsa depolanan değerde birden çok ya da karakter oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="e8d8c-106">Örneğin, değeri <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> olabilir `##main`.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="e8d8c-107">.NET Core 1,0 ' den itibaren, bu özellikler, `#` dizenin başlangıcında zaten varsa `?` saklanan değere artık veya karakterleri içermez.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e8d8c-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e8d8c-108">Version introduced</span></span>

<span data-ttu-id="e8d8c-109">1.0</span><span class="sxs-lookup"><span data-stu-id="e8d8c-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e8d8c-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e8d8c-110">Recommended action</span></span>

<span data-ttu-id="e8d8c-111">Artık özellik değerlerini ayarlarken bu öndeki karakterlerin hiçbirini açıkça kaldırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="e8d8c-112">Bu, özellikle de öndeki `#` veya `?` eklediğiniz her seferinde kaldırmak zorunda olmadığınız için değerleri eklerken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="e8d8c-113">Örneğin, aşağıdaki kod parçacığı .NET Framework ve .NET Core arasındaki davranış farkını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="e8d8c-114">.NET Framework, çıktı olur `????one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="e8d8c-115">.NET Core 'da çıkış `?one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="e8d8c-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="e8d8c-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="e8d8c-116">Category</span></span>

<span data-ttu-id="e8d8c-117">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="e8d8c-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e8d8c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e8d8c-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
