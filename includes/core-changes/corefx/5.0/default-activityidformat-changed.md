---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281320"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="75d71-101">Varsayılan Activityıdformat W3C</span><span class="sxs-lookup"><span data-stu-id="75d71-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="75d71-102">Activity () için varsayılan tanımlayıcı biçimi <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> artık <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="75d71-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="75d71-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="75d71-103">Change description</span></span>

<span data-ttu-id="75d71-104">W3C etkinlik KIMLIĞI biçimi, hiyerarşik KIMLIK biçimine alternatif olarak .NET Core 3,0 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="75d71-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="75d71-105">Ancak, uyumluluğu korumak için, W3C biçimi .NET 5,0 ' e kadar varsayılan olarak yapılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="75d71-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="75d71-106">Varsayılan değer .NET 5,0 ' de değiştirilmiştir, çünkü [W3C biçimi](https://www.w3.org/TR/trace-context/) , birden çok dil uygulamasında daha fazla şekilde kazanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75d71-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="75d71-107">Uygulamanız .NET 5,0 veya sonraki bir sürümü dışında bir platformu hedefliyorsa, bu, varsayılan biçim olan eski davranışla karşılaşacaktır <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> .</span><span class="sxs-lookup"><span data-stu-id="75d71-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="75d71-108">Bu varsayılan, net45 +, Netstandard 1.1 + ve netcoreapp (1. x, 2. x ve 3. x) platformları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="75d71-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="75d71-109">.NET 5,0 ve üzeri sürümlerde, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> olarak ayarlanır <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="75d71-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75d71-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="75d71-110">Version introduced</span></span>

<span data-ttu-id="75d71-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="75d71-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75d71-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="75d71-112">Recommended action</span></span>

<span data-ttu-id="75d71-113">Uygulamanız dağıtılmış izleme için kullanılan tanımlayıcıya belirsiz ise, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="75d71-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="75d71-114">ASP.NET Core gibi kitaplıklar <xref:System.Net.Http.HttpClient> , her iki sürümünü kullanabilir veya yayabilir <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="75d71-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="75d71-115">Mevcut sistemlerle birlikte çalışabilirliğe gerek duyuyorsanız veya geçerli sistemler tanımlayıcı biçimine güvenuygunsa, ' i ' ye ayarlayarak eski davranışı koruyabilirsiniz <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="75d71-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75d71-116">Alternatif olarak, bir AppContext anahtarını üç farklı şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="75d71-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="75d71-117">, Proje dosyasında.</span><span class="sxs-lookup"><span data-stu-id="75d71-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="75d71-118">Dosyasında *runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="75d71-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="75d71-119">Bir ortam değişkeni aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="75d71-119">Through an environment variable.</span></span>

  <span data-ttu-id="75d71-120">`DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` `true` Veya 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="75d71-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="75d71-121">Category</span><span class="sxs-lookup"><span data-stu-id="75d71-121">Category</span></span>

<span data-ttu-id="75d71-122">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="75d71-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75d71-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="75d71-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
