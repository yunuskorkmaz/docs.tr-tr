---
title: .NET CLı ile Kitaplıklar geliştirme
description: .NET CLı kullanarak .NET kitaplıkları oluşturmayı öğrenin. Çoklu çerçeveleri destekleyen bir kitaplık oluşturacaksınız.
author: cartermp
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 5a70cec4a991f673f4d5d3e7b00cd704c6799f47
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512417"
---
# <a name="develop-libraries-with-the-net-cli"></a><span data-ttu-id="72e81-104">.NET CLı ile Kitaplıklar geliştirme</span><span class="sxs-lookup"><span data-stu-id="72e81-104">Develop libraries with the .NET CLI</span></span>

<span data-ttu-id="72e81-105">Bu makalede .NET CLı kullanılarak .NET için kitaplıkların nasıl yazılacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72e81-105">This article covers how to write libraries for .NET using the .NET CLI.</span></span> <span data-ttu-id="72e81-106">CLı, desteklenen tüm işletim sistemlerinde çalışacak etkili ve düşük düzeyde bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="72e81-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="72e81-107">Visual Studio ile Kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim [Visual Studio kılavuzuna başvurur](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="72e81-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72e81-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="72e81-108">Prerequisites</span></span>

<span data-ttu-id="72e81-109">Makinenizde [.NET SDK ve CLI](https://dotnet.microsoft.com/download) yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72e81-109">You need [the .NET SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="72e81-110">Bu belgenin .NET Framework sürümleriyle ilgili bölümlerinde, bir Windows makinesine [.NET Framework](https://dotnet.microsoft.com) yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="72e81-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="72e81-111">Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.net indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)hedefleme paketlerini veya geliştirici paketlerini yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="72e81-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="72e81-112">Bu tabloya başvurun:</span><span class="sxs-lookup"><span data-stu-id="72e81-112">Refer to this table:</span></span>

| <span data-ttu-id="72e81-113">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="72e81-113">.NET Framework version</span></span> | <span data-ttu-id="72e81-114">İndirileceği</span><span class="sxs-lookup"><span data-stu-id="72e81-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="72e81-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="72e81-115">4.6.1</span></span>                  | <span data-ttu-id="72e81-116">.NET Framework 4.6.1 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="72e81-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="72e81-117">4,6</span><span class="sxs-lookup"><span data-stu-id="72e81-117">4.6</span></span>                    | <span data-ttu-id="72e81-118">.NET Framework 4,6 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="72e81-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="72e81-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="72e81-119">4.5.2</span></span>                  | <span data-ttu-id="72e81-120">.NET Framework 4.5.2 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="72e81-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="72e81-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="72e81-121">4.5.1</span></span>                  | <span data-ttu-id="72e81-122">.NET Framework 4.5.1 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="72e81-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="72e81-123">4,5</span><span class="sxs-lookup"><span data-stu-id="72e81-123">4.5</span></span>                    | <span data-ttu-id="72e81-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="72e81-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="72e81-125">4.0</span><span class="sxs-lookup"><span data-stu-id="72e81-125">4.0</span></span>                    | <span data-ttu-id="72e81-126">Windows 7 ve .NET Framework 4 için Windows SDK</span><span class="sxs-lookup"><span data-stu-id="72e81-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="72e81-127">2,0, 3,0 ve 3,5</span><span class="sxs-lookup"><span data-stu-id="72e81-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="72e81-128">.NET Framework 3,5 SP1 çalışma zamanı (veya Windows 8 + sürüm)</span><span class="sxs-lookup"><span data-stu-id="72e81-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-50-or-net-standard"></a><span data-ttu-id="72e81-129">.NET 5,0 veya .NET Standard nasıl hedeflenecek</span><span class="sxs-lookup"><span data-stu-id="72e81-129">How to target .NET 5.0 or .NET Standard</span></span>

<span data-ttu-id="72e81-130">Projenizin hedef çerçevesini proje dosyanıza (*. csproj* veya *. fsproj*) ekleyerek kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-130">You control your project's target framework by adding it to your project file (*.csproj* or *.fsproj*).</span></span> <span data-ttu-id="72e81-131">.NET 5,0 veya .NET Standard hedefleme arasında nasıl seçim yapılacağı hakkında yönergeler için bkz. [.NET 5 ve .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span><span class="sxs-lookup"><span data-stu-id="72e81-131">For guidance on how to choose between targeting .NET 5.0 or .NET Standard see [.NET 5 and .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="72e81-132">.NET Framework sürümleri 4,0 veya sonraki bir sürümü hedeflemek istiyorsanız veya .NET Framework ' de kullanılabilir ancak .NET Standard (örneğin,) bir API kullanmak istiyorsanız, `System.Drawing` aşağıdaki bölümleri okuyun ve çoklu hedef hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="72e81-132">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="72e81-133">Nasıl hedeflenecek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="72e81-133">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="72e81-134">Bu yönergeler makinenizde .NET Framework yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="72e81-134">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="72e81-135">Bağımlılıkları yüklemek için [önkoşulları](#prerequisites) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="72e81-135">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="72e81-136">Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteklenmediğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="72e81-136">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="72e81-137">Desteklenmeyen sürümler hakkında [sss .NET Framework destek yaşam döngüsü ilkesi hakkında SSS](https://support.microsoft.com/gp/framework_faq/en-us) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="72e81-137">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="72e81-138">En fazla geliştirici ve proje sayısına ulaşmak isterseniz, taban çizgisi hedefi olarak .NET Framework 4,0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="72e81-138">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="72e81-139">.NET Framework hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen adını (tfd) kullanarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="72e81-139">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="72e81-140">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="72e81-140">.NET Framework version</span></span> | <span data-ttu-id="72e81-141">TFM</span><span class="sxs-lookup"><span data-stu-id="72e81-141">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="72e81-142">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="72e81-142">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="72e81-143">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="72e81-143">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="72e81-144">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="72e81-144">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="72e81-145">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="72e81-145">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="72e81-146">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="72e81-146">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="72e81-147">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="72e81-147">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="72e81-148">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="72e81-148">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="72e81-149">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="72e81-149">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="72e81-150">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="72e81-150">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="72e81-151">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="72e81-151">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="72e81-152"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="72e81-152">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="72e81-153"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="72e81-153">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="72e81-154">Daha sonra bu tfd 'yi `TargetFramework` proje dosyanızın bölümüne eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-154">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="72e81-155">Örneğin, .NET Framework 4,0 ' i hedefleyen bir kitaplığı nasıl yazacağınız aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="72e81-155">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="72e81-156">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="72e81-156">And that's it!</span></span> <span data-ttu-id="72e81-157">Bu yalnızca .NET Framework 4 için derlense de, kitaplığı .NET Framework daha yeni sürümlerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-157">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="72e81-158">Çoklu hedef</span><span class="sxs-lookup"><span data-stu-id="72e81-158">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="72e81-159">Aşağıdaki yönergelerde .NET Framework makinenizde yüklü olduğunu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="72e81-159">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="72e81-160">Yüklemeniz gereken bağımlılıkları ve bunların nereden indirileceği hakkında bilgi edinmek için [Önkoşullar](#prerequisites) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="72e81-160">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="72e81-161">Projeniz hem .NET Framework hem de .NET ' i desteklediğinde, .NET Framework eski sürümlerini hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-161">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET.</span></span> <span data-ttu-id="72e81-162">Bu senaryoda, daha yeni hedefler için daha yeni API 'Ler ve dil yapıları kullanmak istiyorsanız, `#if` kodunuzda yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="72e81-162">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="72e81-163">Ayrıca, hedeflediğiniz her platform için, her bir durum için gereken farklı API 'Leri dahil etmek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="72e81-163">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="72e81-164">Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="72e81-164">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="72e81-165">.NET Standard ve .NET Framework sürümleri 4,5 veya üzeri için, `HttpClient` ad alanından sınıfını kullanabilirsiniz `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="72e81-165">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="72e81-166">Ancak, .NET Framework önceki sürümleri sınıfına sahip değildir `HttpClient` , `WebClient` Bu nedenle `System.Net` bunun yerine ad alanından sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-166">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="72e81-167">Proje dosyanız şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="72e81-167">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard2.0;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="72e81-168">Burada üç önemli değişiklik fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-168">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="72e81-169">`TargetFramework`Düğüm ile değiştirilmiştir `TargetFrameworks` ve üç tfms içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="72e81-169">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="72e81-170">`<ItemGroup>` `net40` Bir .NET Framework başvurusunda hedef çekme için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="72e81-170">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="72e81-171">`<ItemGroup>` `net45` İki .NET Framework başvuru halinde hedef çekme için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="72e81-171">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="72e81-172">Yapı sistemi, yönergelerden kullanılan aşağıdaki Önişlemci simgelerinden haberdar olur `#if` :</span><span class="sxs-lookup"><span data-stu-id="72e81-172">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="72e81-173">Hedefe göre koşullu derleme kullanan bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="72e81-173">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET Framework 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="72e81-174">Bu projeyi ile oluşturursanız `dotnet build` , klasörün altında üç dizin olduğunu fark edeceksiniz `bin/` :</span><span class="sxs-lookup"><span data-stu-id="72e81-174">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard2.0/
```

<span data-ttu-id="72e81-175">Bunların her biri, `.dll` her bir hedef için dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="72e81-175">Each of these contains the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net"></a><span data-ttu-id="72e81-176">.NET üzerinde kitaplıkları test etme</span><span class="sxs-lookup"><span data-stu-id="72e81-176">How to test libraries on .NET</span></span>

<span data-ttu-id="72e81-177">Platformlar arasında test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72e81-177">It's important to be able to test across platforms.</span></span> <span data-ttu-id="72e81-178">Kutusundan [xUnit](https://xunit.github.io/) veya mstest kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-178">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="72e81-179">Her ikisi de kitaplığınızı .NET 'teki birim testi için uygun şekilde uygundur.</span><span class="sxs-lookup"><span data-stu-id="72e81-179">Both are perfectly suitable for unit testing your library on .NET.</span></span> <span data-ttu-id="72e81-180">Çözümünüzü Test projeleri ile nasıl [ayarlayacağınıza çözümünüzün yapısına](#structuring-a-solution)göre değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="72e81-180">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="72e81-181">Aşağıdaki örnek, test ve kaynak dizinlerinin aynı en üst düzey dizinde canlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="72e81-181">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="72e81-182">Bu bazı [.net CLI](../tools/index.md) komutlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="72e81-182">This uses some [.NET CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="72e81-183">Daha fazla bilgi için bkz. [DotNet New](../tools/dotnet-new.md) ve [DotNet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="72e81-183">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="72e81-184">Çözümünüzü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72e81-184">Set up your solution.</span></span> <span data-ttu-id="72e81-185">Bunu aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-185">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="72e81-186">Bu, projeler oluşturur ve bunları bir çözümde birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="72e81-186">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="72e81-187">Dizininiz şuna `SolutionWithSrcAndTest` benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="72e81-187">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="72e81-188">Test projesinin dizinine gidin ve öğesinden öğesine bir başvuru ekleyin `MyProject.Test` `MyProject` .</span><span class="sxs-lookup"><span data-stu-id="72e81-188">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="72e81-189">Paketleri geri yükle ve projeleri oluştur:</span><span class="sxs-lookup"><span data-stu-id="72e81-189">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

1. <span data-ttu-id="72e81-190">Komutunu yürüterek xUnit 'in çalıştığını doğrulayın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="72e81-190">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="72e81-191">MSTest kullanmayı seçerseniz, bunun yerine MSTest konsol Çalıştırıcısı çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72e81-191">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="72e81-192">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="72e81-192">And that's it!</span></span> <span data-ttu-id="72e81-193">Artık, komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-193">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="72e81-194">Artık her şeyi ayarlamış olduğunuza göre teste devam etmek için, kitaplığınızı test etmek çok basittir:</span><span class="sxs-lookup"><span data-stu-id="72e81-194">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="72e81-195">Kitaplığınızda değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="72e81-195">Make changes to your library.</span></span>
1. <span data-ttu-id="72e81-196">Testleri komut satırından, test dizininizde, `dotnet test` komutuyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72e81-196">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="72e81-197">Komut çağırdığınızda kodunuz otomatik olarak yeniden oluşturulur `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="72e81-197">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="72e81-198">Birden çok proje kullanma</span><span class="sxs-lookup"><span data-stu-id="72e81-198">How to use multiple projects</span></span>

<span data-ttu-id="72e81-199">Daha büyük kitaplıkların yaygın olması, işlevselliği farklı projelere yerleştirbir yerdir.</span><span class="sxs-lookup"><span data-stu-id="72e81-199">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="72e81-200">Idimatik C# ve F # içinde tüketilen bir kitaplık oluşturmak istediğinizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="72e81-200">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="72e81-201">Bu, kitaplığınızın tüketicilerinin C# veya F # için doğal olan yollarla tükettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72e81-201">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="72e81-202">Örneğin, C# ' de, kitaplığı şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-202">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="72e81-203">F # ' da aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="72e81-203">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="72e81-204">Bu gibi tüketim senaryoları, erişildiği API 'Lerin C# ve F # için farklı bir yapıya sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72e81-204">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="72e81-205">Bunu gerçekleştirmeye yönelik yaygın bir yaklaşım, bu temel projeye çağrı yapan API katmanlarını tanımlayan C# ve F # projeleri içeren bir kitaplığın tüm mantığını temel bir projeye katmasıdır.</span><span class="sxs-lookup"><span data-stu-id="72e81-205">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="72e81-206">Bölümün geri kalanı aşağıdaki adları kullanır:</span><span class="sxs-lookup"><span data-stu-id="72e81-206">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="72e81-207">**Awesomelibrary. Core** -kitaplık için tüm mantığı içeren bir çekirdek proje</span><span class="sxs-lookup"><span data-stu-id="72e81-207">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="72e81-208">**Awesomelibrary. CSharp** -C 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #</span><span class="sxs-lookup"><span data-stu-id="72e81-208">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="72e81-209">**Awesomelibrary. FSharp** -F 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #</span><span class="sxs-lookup"><span data-stu-id="72e81-209">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="72e81-210">Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-210">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="72e81-211">Bu, yukarıdaki üç projeyi ve bunları birbirine bağlayan bir çözüm dosyasını ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="72e81-211">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="72e81-212">Çözüm dosyası ve bağlantı projelerinin oluşturulması, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="72e81-212">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="72e81-213">Projeden projeye başvuru</span><span class="sxs-lookup"><span data-stu-id="72e81-213">Project-to-project referencing</span></span>

<span data-ttu-id="72e81-214">Bir projeye başvuru yapmanın en iyi yolu, bir proje başvurusu eklemek için .NET CLı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="72e81-214">The best way to reference a project is to use the .NET CLI to add a project reference.</span></span> <span data-ttu-id="72e81-215">**Awesomelibrary. CSharp** ve **Awesomelibrary. FSharp** proje dizinlerinde aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-215">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="72e81-216">Hem **Awesomelibrary. CSharp** hem de **Awesomelibrary. FSharp** için proje dosyaları artık bir hedef olarak **Awesomelibrary. Core** 'a başvuracaktır `ProjectReference` .</span><span class="sxs-lookup"><span data-stu-id="72e81-216">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="72e81-217">Bunu, proje dosyalarını inceleyerek ve içinde aşağıdakileri görerek doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72e81-217">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="72e81-218">.NET CLı kullanmayı tercih ediyorsanız, bu bölümü her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e81-218">You can add this section to each project file manually if you prefer not to use the .NET CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="72e81-219">Çözüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="72e81-219">Structuring a solution</span></span>

<span data-ttu-id="72e81-220">Çok projeli çözümlerin diğer önemli bir yönü de iyi bir genel proje yapısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="72e81-220">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="72e81-221">İsterseniz kodu düzenleyebilir, ve her bir projeyi çözüm dosyanıza bağladığınızda `dotnet sln add` , `dotnet restore` Çözüm düzeyinde ve ' yi çalıştıracaksınız `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="72e81-221">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
