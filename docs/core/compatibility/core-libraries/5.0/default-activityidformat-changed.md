---
title: 'Son değişiklik: varsayılan Activityıdformat W3C'
description: Varsayılan Activityıdformat artık W3C olan çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: f15c2d61443117cfbcb2be7de9561fecbff9a1d9
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257511"
---
# <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="fde8f-103">Varsayılan ActivityIdFormat W3C</span><span class="sxs-lookup"><span data-stu-id="fde8f-103">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="fde8f-104">Activity () için varsayılan tanımlayıcı biçimi <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> artık <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fde8f-104">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="change-description"></a><span data-ttu-id="fde8f-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="fde8f-105">Change description</span></span>

<span data-ttu-id="fde8f-106">W3C etkinlik KIMLIĞI biçimi, hiyerarşik KIMLIK biçimine alternatif olarak .NET Core 3,0 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fde8f-106">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="fde8f-107">Ancak, uyumluluğu korumak için, W3C biçimi .NET 5,0 ' e kadar varsayılan olarak yapılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="fde8f-107">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="fde8f-108">Varsayılan değer .NET 5 ' te değiştirilmiştir, çünkü [W3C biçimi](https://www.w3.org/TR/trace-context/) , birden çok dil uygulamasında daha fazla şekilde kazanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fde8f-108">The default was changed in .NET 5 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="fde8f-109">Uygulamanız .NET 5 veya sonraki bir sürümünü hedefliyorsa, bu, varsayılan biçim olan eski davranışla karşılaşacaktır <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> .</span><span class="sxs-lookup"><span data-stu-id="fde8f-109">If your app targets a platform other than .NET 5 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="fde8f-110">Bu varsayılan, net45 +, Netstandard 1.1 + ve netcoreapp (1. x, 2. x ve 3. x) platformları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fde8f-110">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="fde8f-111">.NET 5 ve sonraki sürümlerde, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> olarak ayarlanır <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fde8f-111">In .NET 5 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fde8f-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fde8f-112">Version introduced</span></span>

<span data-ttu-id="fde8f-113">5.0</span><span class="sxs-lookup"><span data-stu-id="fde8f-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fde8f-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fde8f-114">Recommended action</span></span>

<span data-ttu-id="fde8f-115">Uygulamanız dağıtılmış izleme için kullanılan tanımlayıcıya belirsiz ise, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fde8f-115">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="fde8f-116">ASP.NET Core gibi kitaplıklar <xref:System.Net.Http.HttpClient> , her iki sürümünü kullanabilir veya yayabilir <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="fde8f-116">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="fde8f-117">Mevcut sistemlerle birlikte çalışabilirliğe gerek duyuyorsanız veya geçerli sistemler tanımlayıcı biçimine güvenuygunsa, ' i ' ye ayarlayarak eski davranışı koruyabilirsiniz <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fde8f-117">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fde8f-118">Alternatif olarak, bir AppContext anahtarını üç farklı şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fde8f-118">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="fde8f-119">, Proje dosyasında.</span><span class="sxs-lookup"><span data-stu-id="fde8f-119">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="fde8f-120">Dosyasında *runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="fde8f-120">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="fde8f-121">Bir ortam değişkeni aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="fde8f-121">Through an environment variable.</span></span>

  <span data-ttu-id="fde8f-122">`DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` `true` Veya 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fde8f-122">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fde8f-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fde8f-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
