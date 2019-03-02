---
title: Platformlar arası araçlarla kitaplıkları ile geliştirme
description: .NET Core CLI araçları ile .NET Core kitaplıkları oluşturmayı öğrenin. Birden çok çerçevelerini destekleyen bir kitaplık oluşturmayı öğreneceksiniz.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 9dd1d8477f8e34e79ff521463972e26a21ad1dfd
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212072"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="68cef-104">Platformlar arası araçlarla kitaplıkları ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="68cef-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="68cef-105">Bu makale için platformlar arası CLI araçları ile .NET kitaplıkları yazma kapsar.</span><span class="sxs-lookup"><span data-stu-id="68cef-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="68cef-106">CLI'yı tüm desteklenen işletim Sistemleri üzerinde çalışan bir verimli ve alt düzey deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68cef-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="68cef-107">Visual Studio ile kitaplıkları yine de oluşturabilir ve bu tercih edilen deneyiminiz olduğu [Visual Studio Kılavuzu'na bakın](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="68cef-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68cef-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="68cef-108">Prerequisites</span></span>

<span data-ttu-id="68cef-109">Gereksinim duyduğunuz [CLI ve .NET Core SDK'sı](https://www.microsoft.com/net/core) makinenizde yüklü.</span><span class="sxs-lookup"><span data-stu-id="68cef-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="68cef-110">Bu belge uğraşmanızı .NET Framework sürümleri için bölümlere gereksinim [.NET Framework](https://dotnet.microsoft.com) bir Windows makinede yüklü.</span><span class="sxs-lookup"><span data-stu-id="68cef-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="68cef-111">Eski .NET Framework hedefleri desteklemek isterseniz, ayrıca, daha eski framework sürümlerini hedefleme Geliştirici paketleri yüklemeniz gerekir [.NET indirme sayfası arşivleri](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="68cef-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="68cef-112">Bu tabloya bakın:</span><span class="sxs-lookup"><span data-stu-id="68cef-112">Refer to this table:</span></span>

| <span data-ttu-id="68cef-113">.NET Framework Sürümü</span><span class="sxs-lookup"><span data-stu-id="68cef-113">.NET Framework Version</span></span> | <span data-ttu-id="68cef-114">Ne yüklemek için</span><span class="sxs-lookup"><span data-stu-id="68cef-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="68cef-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="68cef-115">4.6.1</span></span>                  | <span data-ttu-id="68cef-116">.NET framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="68cef-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="68cef-117">4.6</span><span class="sxs-lookup"><span data-stu-id="68cef-117">4.6</span></span>                    | <span data-ttu-id="68cef-118">.NET framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="68cef-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="68cef-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="68cef-119">4.5.2</span></span>                  | <span data-ttu-id="68cef-120">.NET framework 4.5.2 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="68cef-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="68cef-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="68cef-121">4.5.1</span></span>                  | <span data-ttu-id="68cef-122">.NET framework 4.5.1 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="68cef-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="68cef-123">4,5</span><span class="sxs-lookup"><span data-stu-id="68cef-123">4.5</span></span>                    | <span data-ttu-id="68cef-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="68cef-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="68cef-125">4.0</span><span class="sxs-lookup"><span data-stu-id="68cef-125">4.0</span></span>                    | <span data-ttu-id="68cef-126">Windows Windows 7 ve .NET Framework 4 için SDK'sı</span><span class="sxs-lookup"><span data-stu-id="68cef-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="68cef-127">2.0, 3.0 ve 3.5</span><span class="sxs-lookup"><span data-stu-id="68cef-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="68cef-128">.NET framework 3.5 SP1 çalışma zamanı (veya Windows 8 + sürümü)</span><span class="sxs-lookup"><span data-stu-id="68cef-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="68cef-129">Hedef .NET Standard hakkında</span><span class="sxs-lookup"><span data-stu-id="68cef-129">How to target the .NET Standard</span></span>

<span data-ttu-id="68cef-130">.NET Standard ile oldukça bilgi sahibi değilseniz başvurmak [.NET Standard](../../standard/net-standard.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="68cef-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="68cef-131">Bu makalede, çeşitli uygulamalar için .NET Standard sürümleri eşleyen bir tablo vardır:</span><span class="sxs-lookup"><span data-stu-id="68cef-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="68cef-132">Bu tabloda bir kitaplık oluşturmak amacıyla anlamı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="68cef-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="68cef-133">Bu sürümü .NET standart, çekme en yeni API'ler için erişim ve daha fazla .NET uygulamaları ve .NET Standard sürümlerini hedefleme olanağınız arasında bir denge olacaktır.</span><span class="sxs-lookup"><span data-stu-id="68cef-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="68cef-134">Bir sürümünü seçerek hedeflenebilir platformlara ve sürümlere aralığı kontrol `netstandardX.X` (burada `X.X` bir sürüm numarası) ve proje dosyanıza ekleyerek (`.csproj` veya `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="68cef-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="68cef-135">.NET Standard, ihtiyaçlarınıza bağlı olarak hedeflenirken üç birincil seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="68cef-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="68cef-136">.NET standart - şablonları tarafından sağlanan varsayılan sürümünü kullanabilirsiniz `netstandard1.4` -.NET standart, çoğu API'ları için hala UWP, .NET Framework 4.6.1 ve gelecek .NET Standard 2.0 ile uyumlu olmanın yanı sıra hangi erişmenizi.</span><span class="sxs-lookup"><span data-stu-id="68cef-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="68cef-137">.NET Standard'ın daha düşük veya üzeri bir sürüm değeri değiştirerek kullanabilirsiniz `TargetFramework` proje dosyanızın düğümü.</span><span class="sxs-lookup"><span data-stu-id="68cef-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="68cef-138">.NET standard sürümleri geriye dönük olarak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="68cef-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="68cef-139">Bu anlamına `netstandard1.0` kitaplıkları çalıştıracağınız `netstandard1.1` platformları ve daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="68cef-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="68cef-140">Ancak, hiçbir ileriye dönük bir uyumluluk yoktur - daha düşük bir .NET Standard platformları daha yüksek olanları başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="68cef-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="68cef-141">Diğer bir deyişle `netstandard1.0` kitaplıkları olamaz başvuru hedefleyen kitaplıkları `netstandard1.1` veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="68cef-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="68cef-142">API ve platform desteğiyle gereksinimleriniz için doğru karışımını standart sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="68cef-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="68cef-143">Öneririz `netstandard1.4` şimdilik.</span><span class="sxs-lookup"><span data-stu-id="68cef-143">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="68cef-144">.NET Framework sürüm 4.0 hedeflemek istiyorsanız veya aşağıdaki veya kullanılabilir bir API kullanmak istediğiniz .NET Framework ancak .NET Standard (örneğin, `System.Drawing`), aşağıdaki bölümleri okuyun ve öğrenin multitarget nasıl.</span><span class="sxs-lookup"><span data-stu-id="68cef-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="68cef-145">.NET Framework'ü hedefleyen nasıl</span><span class="sxs-lookup"><span data-stu-id="68cef-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="68cef-146">Bu yönergeler, makinenizde .NET Framework yüklü varsayar.</span><span class="sxs-lookup"><span data-stu-id="68cef-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="68cef-147">Başvurmak [önkoşulları](#prerequisites) yüklü bağımlılıkları almak için.</span><span class="sxs-lookup"><span data-stu-id="68cef-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="68cef-148">Bazı burada kullanılan .NET Framework sürümleri artık desteği olan aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="68cef-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="68cef-149">Başvurmak [.NET Framework desteği yaşam döngüsü ilkesi SSS](https://support.microsoft.com/gp/framework_faq/en-us) desteklenmeyen sürümleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="68cef-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="68cef-150">Geliştiriciler ve projelerle sayısı ulaşmak istiyorsanız, .NET Framework 4.0, temel hedefi olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="68cef-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="68cef-151">.NET Framework'ü hedeflemek için desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef çerçeve adı (TFM) kullanarak başlarsanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="68cef-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

<span data-ttu-id="68cef-152">Ardından bu TFM içine Ekle `TargetFramework` proje dosyanızın bölümü.</span><span class="sxs-lookup"><span data-stu-id="68cef-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="68cef-153">Örneğin, işte .NET Framework 4.0 hedefleyen bir kitaplığı nasıl yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="68cef-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="68cef-154">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="68cef-154">And that's it!</span></span> <span data-ttu-id="68cef-155">Bu yalnızca .NET Framework 4 için derlenmiş olsa da, .NET Framework'ün daha yeni sürümlerinde kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cef-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="68cef-156">Nasıl yapılır Multitarget</span><span class="sxs-lookup"><span data-stu-id="68cef-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="68cef-157">Aşağıdaki yönergeler, .NET Framework'ün makinenizde yüklü olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="68cef-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="68cef-158">Başvurmak [önkoşulları](#prerequisites) bölümü hangi bağımlılıkları yüklemeniz gerekir ve bunları nereden öğrenin.</span><span class="sxs-lookup"><span data-stu-id="68cef-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="68cef-159">.NET Framework ve .NET Core projenizi destekliyorsa, .NET Framework'ün eski sürümlerini hedefleyen gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="68cef-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="68cef-160">Yeni API'ler ve dil yapıları yeni hedeflerini kullanmak istiyorsanız, bu senaryoda kullanma `#if` kodunuzda yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="68cef-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="68cef-161">Farklı bir paket ve bağımlılıkların her çalışması için gereken farklı API'leri dahil etmek için hedeflediğiniz her platform için eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="68cef-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="68cef-162">Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız varsayalım.</span><span class="sxs-lookup"><span data-stu-id="68cef-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="68cef-163">.NET Standard ve .NET Framework sürüm 4.5 veya üstü için kullanabileceğiniz `HttpClient` gelen sınıfı `System.Net.Http` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="68cef-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="68cef-164">Ancak, .NET Framework'ün önceki sürümlerini yok `HttpClient` kullanabilirsiniz, böylece sınıf `WebClient` gelen sınıfı `System.Net` ad alanı olanlar için bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="68cef-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="68cef-165">Proje dosyanız şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="68cef-165">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
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

<span data-ttu-id="68cef-166">Burada üç önemli değişiklikler fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="68cef-167">`TargetFramework` Düğümü tarafından değiştirilmiştir `TargetFrameworks`, ve üç Tfm'ler içindeki ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="68cef-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="68cef-168">Var olan bir `<ItemGroup>` düğümü için `net40` hedef bir .NET Framework başvuru çekmek.</span><span class="sxs-lookup"><span data-stu-id="68cef-168">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="68cef-169">Var olan bir `<ItemGroup>` düğümü için `net45` iki .NET Framework başvurularını çekme hedef.</span><span class="sxs-lookup"><span data-stu-id="68cef-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="68cef-170">Derleme Sistemi kullanılan aşağıdaki önişlemci sembolleri farkında `#if` yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="68cef-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="68cef-171">Koşullu derleme başına-hedef örnek yapmayı kullanımını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="68cef-171">Here is an example making use of conditional compilation per-target:</span></span>

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
        // .NET 4.5+ can use async/await!
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

<span data-ttu-id="68cef-172">Bu proje ile derleme yaparsanız `dotnet build`, üç dizin altında fark edeceksiniz `bin/` klasörü:</span><span class="sxs-lookup"><span data-stu-id="68cef-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="68cef-173">Her birini içeren `.dll` her hedef için dosyaları.</span><span class="sxs-lookup"><span data-stu-id="68cef-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="68cef-174">.NET Core üzerinde kitaplıkları test etme</span><span class="sxs-lookup"><span data-stu-id="68cef-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="68cef-175">Platformlar arasında test edebilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="68cef-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="68cef-176">Kullanabilirsiniz [xUnit](https://xunit.github.io/) veya MSTest hazır.</span><span class="sxs-lookup"><span data-stu-id="68cef-176">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="68cef-177">Her ikisi de, tam birim testi .NET Core kitaplığınızı için uygundur.</span><span class="sxs-lookup"><span data-stu-id="68cef-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="68cef-178">Nasıl çözümünüzü test projeleriyle ayarlayabilirsiniz bağlı olacaktır [çözümünüzün yapısını](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="68cef-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="68cef-179">Aşağıdaki örnek, test ve kaynak dizinleri aynı üst düzey dizininde Canlı varsayar.</span><span class="sxs-lookup"><span data-stu-id="68cef-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="68cef-180">Bu bazı kullanır [.NET Core CLI komutları](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="68cef-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="68cef-181">Bkz: [yeni dotnet](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="68cef-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="68cef-182">Çözümünüzü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="68cef-182">Set up your solution.</span></span> <span data-ttu-id="68cef-183">Bunu aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="68cef-184">Projeleri oluşturmak ve bunları bir çözümde birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cef-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="68cef-185">Dizininiz için `SolutionWithSrcAndTest` şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="68cef-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="68cef-186">Test projesinin dizine gidin ve bir başvuru ekleyin `MyProject.Test` gelen `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="68cef-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="68cef-187">Paketleri geri yükle ve projelerinizi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="68cef-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="68cef-188">Bu xUnit çalıştığını yürüterek doğrulama `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="68cef-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="68cef-189">MSTest kullanmayı seçerseniz, MSTest konsol Çalıştırıcısı yerine çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="68cef-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="68cef-190">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="68cef-190">And that's it!</span></span> <span data-ttu-id="68cef-191">Artık kitaplığınızı komut satırı araçlarını kullanarak tüm platformlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cef-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="68cef-192">Artık her şeyi sahip olduğunuza göre teste devam etmek için ayarlama, kitaplığınıza test çok basittir:</span><span class="sxs-lookup"><span data-stu-id="68cef-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="68cef-193">Kitaplığınıza değişiklikler yapın.</span><span class="sxs-lookup"><span data-stu-id="68cef-193">Make changes to your library.</span></span>
1. <span data-ttu-id="68cef-194">Komut satırından test dizininizde ile testler `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="68cef-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="68cef-195">Çağırdığınızda, kodunuzu otomatik olarak yeniden derlenecek `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="68cef-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="68cef-196">Birden çok proje kullanma</span><span class="sxs-lookup"><span data-stu-id="68cef-196">How to use multiple projects</span></span>

<span data-ttu-id="68cef-197">Daha büyük kitaplıkları için ortak bir gereksinimi, farklı projelerde işlevselliği yerleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="68cef-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="68cef-198">İçinde kullanılan deyimsel tüketilebilecek kitaplık oluşturmak, onlardan Imagine C# ve F#.</span><span class="sxs-lookup"><span data-stu-id="68cef-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="68cef-199">Anlamına kitaplığınızı kullanan Tüketiciler, bunları olduğu için doğal bir şekilde kullandığını C# veya F#.</span><span class="sxs-lookup"><span data-stu-id="68cef-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="68cef-200">Örneğin, C# Kitaplığı gibi bu tükettiğiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="68cef-201">İçinde F#, şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="68cef-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="68cef-202">Erişilen API'leri için farklı bir yapıya sahip olması bu anlama gelir gibi tüketim senaryolar C# ve F#.</span><span class="sxs-lookup"><span data-stu-id="68cef-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="68cef-203">Tüm kitaplık mantığı ile bir çekirdek projeye etkimesi için bu işlemi gerçekleştirmek için yaygın bir yaklaşım olan C# ve F# API tanımlama projeleri Katmanlar bu çağrı, core projesi.</span><span class="sxs-lookup"><span data-stu-id="68cef-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="68cef-204">Bölümün geri kalanında, aşağıdaki adlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="68cef-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="68cef-205">**AwesomeLibrary.Core** -kitaplığının tüm mantığı içeren bir temel proje</span><span class="sxs-lookup"><span data-stu-id="68cef-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="68cef-206">**AwesomeLibrary.CSharp** -C# tüketim yönelik ortak API'ler ile bir proje</span><span class="sxs-lookup"><span data-stu-id="68cef-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="68cef-207">**AwesomeLibrary.FSharp** -ortak sahip bir proje tüketimini API'leri yönelikF#</span><span class="sxs-lookup"><span data-stu-id="68cef-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="68cef-208">Bu kılavuzda aynı yapısını oluşturmak için terminalde aşağıdaki komutları çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="68cef-209">Bu, yukarıdaki üç projeleri ve bunları birbirine bağlayan bir çözüm dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="68cef-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="68cef-210">Çözüm dosyası oluşturma ve bağlama projeleri geri yükleme ve en üst düzey bir proje oluşturmak sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="68cef-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="68cef-211">Projeden projeye başvuru</span><span class="sxs-lookup"><span data-stu-id="68cef-211">Project-to-project referencing</span></span>

<span data-ttu-id="68cef-212">Bir proje başvurusu için en iyi yolu, bir proje başvurusu eklemek için .NET Core CLI kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="68cef-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="68cef-213">Gelen **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinleri, aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="68cef-214">Her ikisi için proje dosyaları **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** artık başvuru olacak **AwesomeLibrary.Core** olarak bir `ProjectReference` hedef.</span><span class="sxs-lookup"><span data-stu-id="68cef-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="68cef-215">Proje dosyalarını incelemek ve bunları aşağıdaki görmeye doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68cef-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="68cef-216">.NET Core CLI'yı kullanmayı tercih ederseniz bu bölümde her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cef-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="68cef-217">Bir çözüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="68cef-217">Structuring a solution</span></span>

<span data-ttu-id="68cef-218">Birden çok proje çözümü başka bir önemli yönüyle iyi bir genel proje yapısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cef-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="68cef-219">Ancak, istediğiniz ve her proje, Çözüm dosyasıyla bağlantı sürece kod düzenleyebilirsiniz `dotnet sln add`, çalıştırmak mümkün olacaktır `dotnet restore` ve `dotnet build` çözüm düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="68cef-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
