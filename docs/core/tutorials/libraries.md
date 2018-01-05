---
title: "Kitaplıklarla platformu araçları arası geliştirme"
description: ".NET Core CLI araçlarını kullanarak .NET için kitaplıkları oluşturmayı öğrenin."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.workload: dotnetcore
ms.openlocfilehash: 8b809fbe73dfd382d568aba5d0f074915d727546
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="8661b-104">Kitaplıklarla platformu araçları arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="8661b-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="8661b-105">Bu makale için platformlar arası CLI araçlarını kullanarak .NET kitaplıkları yazma alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8661b-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="8661b-106">CLI tüm desteklenen işletim Sistemleri arasında çalışan bir verimli ve alt düzey deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8661b-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="8661b-107">Visual Studio ile kitaplıklarını hala oluşturabilirsiniz ve bu tercih edilen deneyiminizi olursa [Visual Studio Kılavuzu'na bakın](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8661b-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8661b-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8661b-108">Prerequisites</span></span>

<span data-ttu-id="8661b-109">Gereksinim duyduğunuz [CLI ve .NET Core SDK](https://www.microsoft.com/net/core) makinenize yüklü.</span><span class="sxs-lookup"><span data-stu-id="8661b-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="8661b-110">.NET Framework sürümleri bu belge postalarla bölümleri için gereksinim duyduğunuz [.NET Framework](http://getdotnet.azurewebsites.net/) bir Windows makinesinde yüklü.</span><span class="sxs-lookup"><span data-stu-id="8661b-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="8661b-111">Eski .NET Framework hedefleri desteklemek istiyorsanız, ek olarak, eski framework sürümlerini hedefleyen Geliştirici paketleri yüklemeniz gerekir [.NET Hedef platformlar sayfası](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="8661b-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="8661b-112">Bu tabloya bakın:</span><span class="sxs-lookup"><span data-stu-id="8661b-112">Refer to this table:</span></span>

| <span data-ttu-id="8661b-113">.NET Framework Sürümü</span><span class="sxs-lookup"><span data-stu-id="8661b-113">.NET Framework Version</span></span> | <span data-ttu-id="8661b-114">Ne karşıdan yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8661b-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="8661b-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="8661b-115">4.6.1</span></span>                  | <span data-ttu-id="8661b-116">.NET framework 4.6.1 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="8661b-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="8661b-117">4.6</span><span class="sxs-lookup"><span data-stu-id="8661b-117">4.6</span></span>                    | <span data-ttu-id="8661b-118">.NET framework 4.6 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="8661b-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="8661b-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="8661b-119">4.5.2</span></span>                  | <span data-ttu-id="8661b-120">.NET framework 4.5.2 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="8661b-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="8661b-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8661b-121">4.5.1</span></span>                  | <span data-ttu-id="8661b-122">.NET framework 4.5.1 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="8661b-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="8661b-123">4,5</span><span class="sxs-lookup"><span data-stu-id="8661b-123">4.5</span></span>                    | <span data-ttu-id="8661b-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="8661b-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="8661b-125">4.0</span><span class="sxs-lookup"><span data-stu-id="8661b-125">4.0</span></span>                    | <span data-ttu-id="8661b-126">Windows 7 ve .NET Framework 4 için Windows SDK</span><span class="sxs-lookup"><span data-stu-id="8661b-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="8661b-127">2.0, 3.0 ve 3.5</span><span class="sxs-lookup"><span data-stu-id="8661b-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="8661b-128">.NET framework 3.5 SP1 çalışma zamanı (veya Windows 8 + sürümü)</span><span class="sxs-lookup"><span data-stu-id="8661b-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="8661b-129">Hedef .NET standart nasıl</span><span class="sxs-lookup"><span data-stu-id="8661b-129">How to target the .NET Standard</span></span>

<span data-ttu-id="8661b-130">Standart .NET oldukça hakkında bilgi sahibi değilseniz, başvurmak [.NET standart](../../standard/net-standard.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8661b-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="8661b-131">Bu makalede, çeşitli uygulamalar için .NET standart sürümleri eşleştiren bir tablo yok:</span><span class="sxs-lookup"><span data-stu-id="8661b-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="8661b-132">Bu tablo bir kitaplığı oluşturmak amacıyla anlamı şudur:</span><span class="sxs-lookup"><span data-stu-id="8661b-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="8661b-133">.NET, çekme standart sürümünü kolaylığını yeni API'lerine erişimi ve daha fazla .NET uygulamaları ve .NET standart sürümlerini hedefleyen olanağı arasında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8661b-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="8661b-134">Bir sürümünü seçerek aralığını targetable platformları ve sürümleri kontrol `netstandardX.X` (burada `X.X` bir sürüm numarası) ve proje dosyanıza ekleme (`.csproj` veya `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="8661b-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="8661b-135">.NET standart, ihtiyaçlarınıza bağlı olarak hedeflerken üç birincil seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="8661b-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="8661b-136">.NET standart - şablonları tarafından sağlanan varsayılan sürümü kullanabilirsiniz `netstandard1.4` -e .NET standart çoğu API'leri hala UWP, .NET Framework 4.6.1 ve gelecek .NET standart 2.0 ile uyumlu devam ederken hangi erişmenizi.</span><span class="sxs-lookup"><span data-stu-id="8661b-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="8661b-137">Bir veya daha küçük sürümü .NET standart değerini değiştirerek kullanabilirsiniz `TargetFramework` proje dosyanızın düğümü.</span><span class="sxs-lookup"><span data-stu-id="8661b-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="8661b-138">Geriye dönük olarak uyumlu .NET standart sürümleri.</span><span class="sxs-lookup"><span data-stu-id="8661b-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="8661b-139">Anlamına `netstandard1.0` kitaplıkları çalıştıracağınız `netstandard1.1` platformları ve daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="8661b-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="8661b-140">Ancak, ileriye dönük bir uyumluluk yoktur - alt .NET standart platformları yüksek olanları başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="8661b-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="8661b-141">Bunun anlamı `netstandard1.0` kitaplıkları olamaz başvuru hedefleyen kitaplıkları `netstandard1.1` ya da daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="8661b-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="8661b-142">API ve platform desteği gereksinimleriniz için doğru karışımını standart sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="8661b-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="8661b-143">Öneririz `netstandard1.4` şimdilik.</span><span class="sxs-lookup"><span data-stu-id="8661b-143">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="8661b-144">.NET Framework sürüm 4.0 hedef istiyorsanız veya aşağıdaki veya kullanılabilir bir API kullanmak istediğiniz .NET Framework ancak .NET standart (örneğin, `System.Drawing`), aşağıdaki bölümleri okuyun ve bilgi multitarget nasıl.</span><span class="sxs-lookup"><span data-stu-id="8661b-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="8661b-145">Hedef .NET Framework'ü nasıl</span><span class="sxs-lookup"><span data-stu-id="8661b-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="8661b-146">Bu yönergeler, makinenizde .NET Framework yüklü varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8661b-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="8661b-147">Başvurmak [Önkoşullar](#prerequisites) yüklü bağımlılıkları alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="8661b-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="8661b-148">Burada kullanılan .NET Framework sürümleri bazıları artık desteği olan aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8661b-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="8661b-149">Başvurmak [.NET Framework destek yaşam döngüsü ilkesi SSS](https://support.microsoft.com/gp/framework_faq/en-us) desteklenmeyen sürümleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="8661b-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="8661b-150">Maksimum sayısını geliştiriciler ve projeleri erişmek isterseniz, .NET Framework 4.0 temel hedefi olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="8661b-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="8661b-151">.NET Framework hedeflemek için desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen ad (TFM) kullanarak başlayın gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="8661b-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

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

<span data-ttu-id="8661b-152">Ardından bu TFM içine ekleme `TargetFramework` proje dosyanızı bölümü.</span><span class="sxs-lookup"><span data-stu-id="8661b-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="8661b-153">Örneğin, işte .NET Framework 4.0 hedefleyen bir kitaplık nasıl yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="8661b-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="8661b-154">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="8661b-154">And that's it!</span></span> <span data-ttu-id="8661b-155">Bu yalnızca .NET Framework 4 için derlenmiş rağmen .NET Framework'ün daha yeni sürümlerinde kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8661b-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="8661b-156">Multitarget nasıl</span><span class="sxs-lookup"><span data-stu-id="8661b-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="8661b-157">Aşağıdaki yönergeler, makinenizde .NET Framework yüklü varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8661b-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="8661b-158">Başvurmak [Önkoşullar](#prerequisites) yüklemeniz gereken hangi bağımlılıkları ve bunları indirmek nereye öğrenmek için bölüm.</span><span class="sxs-lookup"><span data-stu-id="8661b-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="8661b-159">Projeniz .NET Framework ve .NET Core desteklediğinde .NET Framework'ün daha eski sürümlerini hedefleyen gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8661b-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="8661b-160">Bu senaryoda, yeni API'ları ve dil yapıları için daha yeni hedefleri kullanmak istiyorsanız, kullanmak `#if` kodunuzda yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="8661b-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="8661b-161">Ayrıca farklı paketler ve bağımlılıklar her örneği için gereken farklı API'leri dahil etmek için hedefleme her platform için eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8661b-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="8661b-162">Örneğin, HTTP üzerinden ağ işlemlerini gerçekleştiren bir kitaplığınız varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8661b-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="8661b-163">.NET standart ve .NET Framework sürüm 4.5 veya üstü için kullanabileceğiniz `HttpClient` sınıfıyla `System.Net.Http` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8661b-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="8661b-164">Ancak, .NET Framework'ün önceki sürümlerinde yok `HttpClient` kullanabileceğinizi nedenle `WebClient` sınıfıyla `System.Net` ad alanı olanlar için bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="8661b-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="8661b-165">Proje dosyanızı şöyle:</span><span class="sxs-lookup"><span data-stu-id="8661b-165">Your project file could look like this:</span></span>

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

<span data-ttu-id="8661b-166">Burada üç önemli değişiklikler fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="8661b-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="8661b-167">`TargetFramework` Düğümü tarafından değiştirildi `TargetFrameworks`, ve üç TFMs içinde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="8661b-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="8661b-168">Var olan bir `<ItemGroup>` düğümü için `net40 ` bir .NET Framework başvurusundan çekme hedef.</span><span class="sxs-lookup"><span data-stu-id="8661b-168">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="8661b-169">Var olan bir `<ItemGroup>` düğümü için `net45` iki .NET Framework başvurularında çekme hedef.</span><span class="sxs-lookup"><span data-stu-id="8661b-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="8661b-170">Derleme Sistemi kullanılan aşağıdaki önişlemci simgelerin bilmez `#if` yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="8661b-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="8661b-171">Koşullu derleme başına-hedef örnek yapmayı kullanımını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="8661b-171">Here is an example making use of conditional compilation per-target:</span></span>

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
            string url = "http://www.dotnetfoundation.org/";

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
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="8661b-172">Bu proje ile yapı `dotnet build`, üç dizinlerde fark edeceksiniz `bin/` klasörü:</span><span class="sxs-lookup"><span data-stu-id="8661b-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="8661b-173">Bunların her birini içeren `.dll` dosyaları her hedef için.</span><span class="sxs-lookup"><span data-stu-id="8661b-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="8661b-174">.NET Core üzerinde kitaplıkları test etme</span><span class="sxs-lookup"><span data-stu-id="8661b-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="8661b-175">Platformlar arası test edebilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8661b-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="8661b-176">Kullanabilirsiniz [xUnit](http://xunit.github.io/) veya mstest'i kutuda dışında.</span><span class="sxs-lookup"><span data-stu-id="8661b-176">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="8661b-177">Her ikisi de, mükemmel birim kitaplığınızı .NET Core testi için uygundur.</span><span class="sxs-lookup"><span data-stu-id="8661b-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="8661b-178">Nasıl test projeleri çözümünüzle ayarlamanız bağlıdır [çözümünüzün yapısını](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="8661b-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="8661b-179">Aşağıdaki örnek, test ve kaynak dizinler aynı üst düzey dizinde Canlı varsayar.</span><span class="sxs-lookup"><span data-stu-id="8661b-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="8661b-180">Bu, bazı kullanır [.NET Core CLI komutları](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="8661b-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="8661b-181">Bkz: [dotnet yeni](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8661b-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="8661b-182">Çözümünüzü ayarlarken ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8661b-182">Set up your solution.</span></span> <span data-ttu-id="8661b-183">Aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8661b-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="8661b-184">Projeleri oluşturmak ve bunları bir çözümde birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8661b-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="8661b-185">Dizininiz için `SolutionWithSrcAndTest` aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="8661b-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="8661b-186">Test projesinin dizinine gidin ve bir başvuru ekleyin `MyProject.Test` gelen `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="8661b-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="8661b-187">Paketler geri ve projeleri oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8661b-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="8661b-188">Bu xUnit çalıştıran yürüterek doğrulayın `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="8661b-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="8661b-189">Mstest'i kullanmayı seçerseniz, mstest'i konsol Çalıştırıcısı yerine çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8661b-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="8661b-190">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="8661b-190">And that's it!</span></span> <span data-ttu-id="8661b-191">Komut satırı araçlarını kullanarak tüm platformlarda kitaplığınızın artık test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8661b-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="8661b-192">Her şeyi sahip olduğunuza göre teste devam etmek için ayarlama, kitaplığınızın sınama çok basittir:</span><span class="sxs-lookup"><span data-stu-id="8661b-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="8661b-193">Değişiklikleri kitaplığınıza yapın.</span><span class="sxs-lookup"><span data-stu-id="8661b-193">Make changes to your library.</span></span>
1. <span data-ttu-id="8661b-194">Komut satırından test dizininize ile testleri `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="8661b-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="8661b-195">Çağırdığınızda, kodunuzu otomatik olarak yeniden oluşturulacak `dotnet test` komutu.</span><span class="sxs-lookup"><span data-stu-id="8661b-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="8661b-196">Birden çok proje kullanma</span><span class="sxs-lookup"><span data-stu-id="8661b-196">How to use multiple projects</span></span>

<span data-ttu-id="8661b-197">Bir ortak büyük kitaplıkları için farklı projelerde işlevselliği yerleştirmek için gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="8661b-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="8661b-198">Kullanılan deyimsel C# ve F # içinde kullanılabilecek bir kitaplık oluşturmak istediğinizde düşünün.</span><span class="sxs-lookup"><span data-stu-id="8661b-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="8661b-199">Bu, Tüketicileri kitaplığınızın bunları C# veya F # için doğal şekilde kullandığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8661b-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="8661b-200">Örneğin, C# dilinde, bu gibi kitaplık tüketebilir:</span><span class="sxs-lookup"><span data-stu-id="8661b-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="8661b-201">F #'ta, şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="8661b-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="8661b-202">Tüketim senaryoları erişilen API'ları C# ve F # için farklı bir yapıya sahip olmanız bu ortalama ister.</span><span class="sxs-lookup"><span data-stu-id="8661b-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="8661b-203">Bu işlemi gerçekleştirmek için bir ortak tüm kitaplık mantığı, çekirdek projeye çağrı API katmanları tanımlama C# ve F # projeleri ile bir çekirdek projesine faktörü yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8661b-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="8661b-204">Bölümün geri kalanında aşağıdaki adları kullanır:</span><span class="sxs-lookup"><span data-stu-id="8661b-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="8661b-205">**AwesomeLibrary.Core** -kitaplık için tüm mantığı içeren bir çekirdek projesi</span><span class="sxs-lookup"><span data-stu-id="8661b-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="8661b-206">**AwesomeLibrary.CSharp** -C# kullanımına yönelik ortak API'ler sahip bir proje</span><span class="sxs-lookup"><span data-stu-id="8661b-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="8661b-207">**AwesomeLibrary.FSharp** -F # tüketimini yönelik ortak API'ler sahip bir proje</span><span class="sxs-lookup"><span data-stu-id="8661b-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="8661b-208">Bu kılavuzda aynı yapısını oluşturmak üzere, terminalde aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8661b-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="8661b-209">Bu, yukarıdaki üç projeleri ve birbirine bağlayan bir çözüm dosyasını ekler.</span><span class="sxs-lookup"><span data-stu-id="8661b-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="8661b-210">Çözüm dosyası oluşturma ve projeleri bağlama geri yüklemek ve bir üst düzey projelerden yapı olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8661b-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="8661b-211">Proje projesine başvurma</span><span class="sxs-lookup"><span data-stu-id="8661b-211">Project-to-project referencing</span></span>

<span data-ttu-id="8661b-212">Bir proje başvurusu için en iyi yolu, proje başvurusu eklemek için .NET Core CLI kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8661b-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="8661b-213">Gelen **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinler, aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8661b-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="8661b-214">Her ikisi için proje dosyalarını **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** şimdi başvuru olacaktır **AwesomeLibrary.Core** olarak bir `ProjectReference` hedef.</span><span class="sxs-lookup"><span data-stu-id="8661b-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="8661b-215">Proje dosyalarını denetleyerek ve bunları aşağıdakileri görmesini doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8661b-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="8661b-216">.NET Core CLI kullanmayı tercih ederseniz, bu bölümde her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8661b-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="8661b-217">Çözüm yapısı</span><span class="sxs-lookup"><span data-stu-id="8661b-217">Structuring a solution</span></span>

<span data-ttu-id="8661b-218">Başka bir önemli özelliği birden çok proje çözümü, iyi bir genel proje yapı saptamaktır.</span><span class="sxs-lookup"><span data-stu-id="8661b-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="8661b-219">Ancak, istediğiniz ve çözüm dosyanızla her proje bağlamak sürece kodu düzenleyebilirsiniz `dotnet sln add`, çalıştırmanız mümkün olacaktır `dotnet restore` ve `dotnet build` çözüm düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="8661b-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
