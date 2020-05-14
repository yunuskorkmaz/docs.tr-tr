---
title: .NET Core CLI ile Kitaplıklar geliştirin
description: .NET Core CLI kullanarak .NET Core kitaplıkları oluşturmayı öğrenin. Çoklu çerçeveleri destekleyen bir kitaplık oluşturacaksınız.
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: 7aadaf7bf7819d52a57c3a137beff46d924d8cb0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396210"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="6fc3b-104">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="6fc3b-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="6fc3b-105">Bu makalede, .NET Core CLI kullanarak .NET için kitaplıkların nasıl yazılacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="6fc3b-106">CLı, desteklenen tüm işletim sistemlerinde çalışacak etkili ve düşük düzeyde bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="6fc3b-107">Visual Studio ile Kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim [Visual Studio kılavuzuna başvurur](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6fc3b-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fc3b-108">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="6fc3b-108">Prerequisites</span></span>

<span data-ttu-id="6fc3b-109">Makinenizde yüklü [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="6fc3b-110">Bu belgenin .NET Framework sürümleriyle ilgili bölümlerinde, bir Windows makinesine [.NET Framework](https://dotnet.microsoft.com) yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="6fc3b-111">Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.net indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)hedefleme paketlerini veya geliştirici paketlerini yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="6fc3b-112">Bu tabloya başvurun:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-112">Refer to this table:</span></span>

| <span data-ttu-id="6fc3b-113">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="6fc3b-113">.NET Framework version</span></span> | <span data-ttu-id="6fc3b-114">İndirileceği</span><span class="sxs-lookup"><span data-stu-id="6fc3b-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="6fc3b-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6fc3b-115">4.6.1</span></span>                  | <span data-ttu-id="6fc3b-116">.NET Framework 4.6.1 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="6fc3b-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="6fc3b-117">4.6</span><span class="sxs-lookup"><span data-stu-id="6fc3b-117">4.6</span></span>                    | <span data-ttu-id="6fc3b-118">.NET Framework 4,6 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="6fc3b-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="6fc3b-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="6fc3b-119">4.5.2</span></span>                  | <span data-ttu-id="6fc3b-120">.NET Framework 4.5.2 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="6fc3b-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="6fc3b-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6fc3b-121">4.5.1</span></span>                  | <span data-ttu-id="6fc3b-122">.NET Framework 4.5.1 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="6fc3b-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="6fc3b-123">4,5</span><span class="sxs-lookup"><span data-stu-id="6fc3b-123">4.5</span></span>                    | <span data-ttu-id="6fc3b-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="6fc3b-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="6fc3b-125">4.0</span><span class="sxs-lookup"><span data-stu-id="6fc3b-125">4.0</span></span>                    | <span data-ttu-id="6fc3b-126">Windows 7 ve .NET Framework 4 için Windows SDK</span><span class="sxs-lookup"><span data-stu-id="6fc3b-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="6fc3b-127">2,0, 3,0 ve 3,5</span><span class="sxs-lookup"><span data-stu-id="6fc3b-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="6fc3b-128">.NET Framework 3,5 SP1 çalışma zamanı (veya Windows 8 + sürüm)</span><span class="sxs-lookup"><span data-stu-id="6fc3b-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="6fc3b-129">.NET Standard nasıl hedeflenecek</span><span class="sxs-lookup"><span data-stu-id="6fc3b-129">How to target the .NET Standard</span></span>

<span data-ttu-id="6fc3b-130">.NET Standard hakkında bilginiz yoksa daha fazla bilgi edinmek için [.NET Standard](../../standard/net-standard.md) başvurun.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="6fc3b-131">Bu makalede, .NET Standard sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="6fc3b-132">Bu tabloda kitaplık oluşturma amaçları için ne olacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="6fc3b-133">Seçtiğiniz .NET Standard sürümü, en yeni API 'lere erişim ve daha fazla .NET uygulaması ve .NET Standard sürümlerini hedefleyebilme arasında bir zorunluluğunu getirir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="6fc3b-134">Bir sürümünü `netstandardX.X` ( `X.X` sürüm numarası) seçerek ve proje dosyanıza (veya) ekleyerek hedeflenebilir platformlarının ve sürümlerinin aralığını kontrol edersiniz `.csproj` `.fsproj` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="6fc3b-135">Gereksinimlerinize bağlı olarak .NET Standard hedeflemek için üç birincil seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="6fc3b-136">`netstandard1.4`.NET Standard ' de UWP, .NET Framework 4.6.1 ve .NET Standard 2,0 ile uyumlu olmaya devam ederken birçok API 'ye erişmenizi sağlayan şablonlar tarafından sağlanan .NET Standard varsayılan sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="6fc3b-137">.NET Standard daha düşük veya daha yüksek bir sürümünü, `TargetFramework` proje dosyanızın düğümündeki değeri değiştirerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="6fc3b-138">.NET Standard sürümler geriye dönük olarak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="6fc3b-139">Bu, `netstandard1.0` kitaplıkların `netstandard1.1` platformlar ve daha yükseği üzerinde çalıştığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="6fc3b-140">Ancak, ileri bir uyumluluk yoktur.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="6fc3b-141">Daha düşük .NET Standard platformlar daha fazla başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="6fc3b-142">Bu, `netstandard1.0` kitaplıkların, veya üzeri kitaplıklara başvurmayacağı anlamına gelir `netstandard1.1` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="6fc3b-143">Gereksinimlerinize uygun API 'lerin ve platform desteğinin doğru karışımına sahip standart sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="6fc3b-144">Şimdilik önerilir `netstandard1.4` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="6fc3b-145">.NET Framework sürümleri 4,0 veya sonraki bir sürümü hedeflemek istiyorsanız veya .NET Framework ' de kullanılabilir ancak .NET Standard (örneğin,) bir API kullanmak istiyorsanız, `System.Drawing` aşağıdaki bölümleri okuyun ve çoklu hedef hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="6fc3b-146">Nasıl hedeflenecek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6fc3b-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="6fc3b-147">Bu yönergeler makinenizde .NET Framework yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="6fc3b-148">Bağımlılıkları yüklemek için [önkoşulları](#prerequisites) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="6fc3b-149">Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteklenmediğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="6fc3b-150">Desteklenmeyen sürümler hakkında [sss .NET Framework destek yaşam döngüsü ilkesi hakkında SSS](https://support.microsoft.com/gp/framework_faq/en-us) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="6fc3b-151">En fazla geliştirici ve proje sayısına ulaşmak isterseniz, taban çizgisi hedefi olarak .NET Framework 4,0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="6fc3b-152">.NET Framework hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen adını (tfd) kullanarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="6fc3b-153">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="6fc3b-153">.NET Framework version</span></span> | <span data-ttu-id="6fc3b-154">TFM</span><span class="sxs-lookup"><span data-stu-id="6fc3b-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="6fc3b-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="6fc3b-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="6fc3b-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="6fc3b-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="6fc3b-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="6fc3b-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="6fc3b-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="6fc3b-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="6fc3b-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="6fc3b-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="6fc3b-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="6fc3b-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="6fc3b-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="6fc3b-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="6fc3b-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="6fc3b-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="6fc3b-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="6fc3b-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="6fc3b-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6fc3b-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="6fc3b-165"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="6fc3b-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="6fc3b-166"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="6fc3b-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="6fc3b-167">Daha sonra bu tfd 'yi `TargetFramework` proje dosyanızın bölümüne eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="6fc3b-168">Örneğin, .NET Framework 4,0 ' i hedefleyen bir kitaplığı nasıl yazacağınız aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6fc3b-169">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="6fc3b-169">And that's it!</span></span> <span data-ttu-id="6fc3b-170">Bu yalnızca .NET Framework 4 için derlense de, kitaplığı .NET Framework daha yeni sürümlerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="6fc3b-171">Çoklu hedef</span><span class="sxs-lookup"><span data-stu-id="6fc3b-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="6fc3b-172">Aşağıdaki yönergelerde .NET Framework makinenizde yüklü olduğunu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="6fc3b-173">Yüklemeniz gereken bağımlılıkları ve bunların nereden indirileceği hakkında bilgi edinmek için [Önkoşullar](#prerequisites) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="6fc3b-174">Projeniz hem .NET Framework hem de .NET Core ' u desteklediğinde, .NET Framework eski sürümlerini hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="6fc3b-175">Bu senaryoda, daha yeni hedefler için daha yeni API 'Ler ve dil yapıları kullanmak istiyorsanız, `#if` kodunuzda yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="6fc3b-176">Ayrıca, hedeflediğiniz her platform için, her bir durum için gereken farklı API 'Leri dahil etmek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="6fc3b-177">Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="6fc3b-178">.NET Standard ve .NET Framework sürümleri 4,5 veya üzeri için, `HttpClient` ad alanından sınıfını kullanabilirsiniz `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="6fc3b-179">Ancak, .NET Framework önceki sürümleri sınıfına sahip değildir `HttpClient` , `WebClient` Bu nedenle `System.Net` bunun yerine ad alanından sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="6fc3b-180">Proje dosyanız şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="6fc3b-181">Burada üç önemli değişiklik fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="6fc3b-182">`TargetFramework`Düğüm ile değiştirilmiştir `TargetFrameworks` ve üç tfms içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="6fc3b-183">`<ItemGroup>` `net40` Bir .NET Framework başvurusunda hedef çekme için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="6fc3b-184">`<ItemGroup>` `net45` İki .NET Framework başvuru halinde hedef çekme için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="6fc3b-185">Yapı sistemi, yönergelerden kullanılan aşağıdaki Önişlemci simgelerinden haberdar olur `#if` :</span><span class="sxs-lookup"><span data-stu-id="6fc3b-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="6fc3b-186">Hedefe göre koşullu derleme kullanan bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="6fc3b-187">Bu projeyi ile oluşturursanız `dotnet build` , klasörün altında üç dizin olduğunu fark edeceksiniz `bin/` :</span><span class="sxs-lookup"><span data-stu-id="6fc3b-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="6fc3b-188">Bunların her biri, `.dll` her bir hedef için dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="6fc3b-189">.NET Core 'da kitaplıkları test etme</span><span class="sxs-lookup"><span data-stu-id="6fc3b-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="6fc3b-190">Platformlar arasında test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="6fc3b-191">Kutusundan [xUnit](https://xunit.github.io/) veya mstest kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="6fc3b-192">Her ikisi de kitaplığınızın .NET Core 'da birim testi için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="6fc3b-193">Çözümünüzü Test projeleri ile nasıl [ayarlayacağınıza çözümünüzün yapısına](#structuring-a-solution)göre değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="6fc3b-194">Aşağıdaki örnek, test ve kaynak dizinlerinin aynı en üst düzey dizinde canlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="6fc3b-195">Bu, bazı [.NET Core CLI](../tools/index.md) komutlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="6fc3b-196">Daha fazla bilgi için bkz. [DotNet New](../tools/dotnet-new.md) ve [DotNet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="6fc3b-197">Çözümünüzü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-197">Set up your solution.</span></span> <span data-ttu-id="6fc3b-198">Bunu aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="6fc3b-199">Bu, projeler oluşturur ve bunları bir çözümde birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="6fc3b-200">Dizininiz şuna `SolutionWithSrcAndTest` benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="6fc3b-201">Test projesinin dizinine gidin ve öğesinden öğesine bir başvuru ekleyin `MyProject.Test` `MyProject` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="6fc3b-202">Paketleri geri yükle ve projeleri oluştur:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="6fc3b-203">Komutunu yürüterek xUnit 'in çalıştığını doğrulayın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="6fc3b-204">MSTest kullanmayı seçerseniz, bunun yerine MSTest konsol Çalıştırıcısı çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="6fc3b-205">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="6fc3b-205">And that's it!</span></span> <span data-ttu-id="6fc3b-206">Artık, komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="6fc3b-207">Artık her şeyi ayarlamış olduğunuza göre teste devam etmek için, kitaplığınızı test etmek çok basittir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="6fc3b-208">Kitaplığınızda değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-208">Make changes to your library.</span></span>
1. <span data-ttu-id="6fc3b-209">Testleri komut satırından, test dizininizde, `dotnet test` komutuyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="6fc3b-210">Komut çağırdığınızda kodunuz otomatik olarak yeniden oluşturulur `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="6fc3b-211">Birden çok proje kullanma</span><span class="sxs-lookup"><span data-stu-id="6fc3b-211">How to use multiple projects</span></span>

<span data-ttu-id="6fc3b-212">Daha büyük kitaplıkların yaygın olması, işlevselliği farklı projelere yerleştirbir yerdir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="6fc3b-213">Idimatik C# ve F # içinde tüketilen bir kitaplık oluşturmak istediğinizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="6fc3b-214">Bu, kitaplığınızın tüketicilerinin C# veya F # için doğal olan yollarla tükettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="6fc3b-215">Örneğin, C# ' de, kitaplığı şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="6fc3b-216">F # ' da aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="6fc3b-217">Bu gibi tüketim senaryoları, erişildiği API 'Lerin C# ve F # için farklı bir yapıya sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="6fc3b-218">Bunu gerçekleştirmeye yönelik yaygın bir yaklaşım, bu temel projeye çağrı yapan API katmanlarını tanımlayan C# ve F # projeleri içeren bir kitaplığın tüm mantığını temel bir projeye katmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="6fc3b-219">Bölümün geri kalanı aşağıdaki adları kullanır:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="6fc3b-220">**Awesomelibrary. Core** -kitaplık için tüm mantığı içeren bir çekirdek proje</span><span class="sxs-lookup"><span data-stu-id="6fc3b-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="6fc3b-221">**Awesomelibrary. CSharp** -C 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #</span><span class="sxs-lookup"><span data-stu-id="6fc3b-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="6fc3b-222">**Awesomelibrary. FSharp** -F 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #</span><span class="sxs-lookup"><span data-stu-id="6fc3b-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="6fc3b-223">Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="6fc3b-224">Bu, yukarıdaki üç projeyi ve bunları birbirine bağlayan bir çözüm dosyasını ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="6fc3b-225">Çözüm dosyası ve bağlantı projelerinin oluşturulması, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="6fc3b-226">Projeden projeye başvuru</span><span class="sxs-lookup"><span data-stu-id="6fc3b-226">Project-to-project referencing</span></span>

<span data-ttu-id="6fc3b-227">Bir projeye başvurmak için en iyi yöntem .NET Core CLI bir proje başvurusu eklemek için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="6fc3b-228">**Awesomelibrary. CSharp** ve **Awesomelibrary. FSharp** proje dizinlerinde aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="6fc3b-229">Hem **Awesomelibrary. CSharp** hem de **Awesomelibrary. FSharp** için proje dosyaları artık bir hedef olarak **Awesomelibrary. Core** 'a başvuracaktır `ProjectReference` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="6fc3b-230">Bunu, proje dosyalarını inceleyerek ve içinde aşağıdakileri görerek doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6fc3b-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="6fc3b-231">.NET Core CLI kullanmayı tercih ediyorsanız, bu bölümü her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="6fc3b-232">Çözüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6fc3b-232">Structuring a solution</span></span>

<span data-ttu-id="6fc3b-233">Çok projeli çözümlerin diğer önemli bir yönü de iyi bir genel proje yapısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="6fc3b-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="6fc3b-234">İsterseniz kodu düzenleyebilir, ve her bir projeyi çözüm dosyanıza bağladığınızda `dotnet sln add` , `dotnet restore` Çözüm düzeyinde ve ' yi çalıştıracaksınız `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="6fc3b-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
