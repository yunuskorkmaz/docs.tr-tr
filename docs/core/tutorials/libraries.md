---
title: Platformlar Arası Araçlarla Kitaplık Geliştirme
description: .NET Core CLI araçlarını kullanarak .NET Core kitaplıkları oluşturmayı öğrenin. Çoklu çerçeveleri destekleyen bir kitaplık oluşturacaksınız.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: dcd454f0bd1739597fc27dccf2849fc259767292
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420466"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="41a44-104">Platformlar Arası Araçlarla Kitaplık Geliştirme</span><span class="sxs-lookup"><span data-stu-id="41a44-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="41a44-105">Bu makalede, platformlar arası CLı araçları kullanılarak .NET için kitaplıkların nasıl yazılacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41a44-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="41a44-106">CLı, desteklenen tüm işletim sistemlerinde çalışacak etkili ve düşük düzeyde bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="41a44-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="41a44-107">Visual Studio ile Kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim [Visual Studio kılavuzuna başvurur](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="41a44-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41a44-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="41a44-108">Prerequisites</span></span>

<span data-ttu-id="41a44-109">Makinenizde yüklü [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41a44-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="41a44-110">Bu belgenin .NET Framework sürümleriyle ilgili bölümlerinde, bir Windows makinesine [.NET Framework](https://dotnet.microsoft.com) yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41a44-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="41a44-111">Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.net indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)eski Framework sürümleri için hedefleme/geliştirici paketleri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="41a44-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="41a44-112">Bu tabloya başvurun:</span><span class="sxs-lookup"><span data-stu-id="41a44-112">Refer to this table:</span></span>

| <span data-ttu-id="41a44-113">.NET Framework Sürümü</span><span class="sxs-lookup"><span data-stu-id="41a44-113">.NET Framework Version</span></span> | <span data-ttu-id="41a44-114">İndirileceği</span><span class="sxs-lookup"><span data-stu-id="41a44-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="41a44-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="41a44-115">4.6.1</span></span>                  | <span data-ttu-id="41a44-116">.NET Framework 4.6.1 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="41a44-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="41a44-117">4.6</span><span class="sxs-lookup"><span data-stu-id="41a44-117">4.6</span></span>                    | <span data-ttu-id="41a44-118">.NET Framework 4,6 hedefleme paketi</span><span class="sxs-lookup"><span data-stu-id="41a44-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="41a44-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="41a44-119">4.5.2</span></span>                  | <span data-ttu-id="41a44-120">.NET Framework 4.5.2 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="41a44-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="41a44-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="41a44-121">4.5.1</span></span>                  | <span data-ttu-id="41a44-122">.NET Framework 4.5.1 Geliştirici paketi</span><span class="sxs-lookup"><span data-stu-id="41a44-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="41a44-123">4,5</span><span class="sxs-lookup"><span data-stu-id="41a44-123">4.5</span></span>                    | <span data-ttu-id="41a44-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="41a44-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="41a44-125">4.0</span><span class="sxs-lookup"><span data-stu-id="41a44-125">4.0</span></span>                    | <span data-ttu-id="41a44-126">Windows 7 ve .NET Framework 4 için Windows SDK</span><span class="sxs-lookup"><span data-stu-id="41a44-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="41a44-127">2,0, 3,0 ve 3,5</span><span class="sxs-lookup"><span data-stu-id="41a44-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="41a44-128">.NET Framework 3,5 SP1 çalışma zamanı (veya Windows 8 + sürüm)</span><span class="sxs-lookup"><span data-stu-id="41a44-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="41a44-129">.NET Standard nasıl hedeflenecek</span><span class="sxs-lookup"><span data-stu-id="41a44-129">How to target the .NET Standard</span></span>

<span data-ttu-id="41a44-130">.NET Standard hakkında tam bilginiz yoksa daha fazla bilgi edinmek için [.NET Standard](../../standard/net-standard.md) başvurun.</span><span class="sxs-lookup"><span data-stu-id="41a44-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="41a44-131">Bu makalede, .NET Standard sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:</span><span class="sxs-lookup"><span data-stu-id="41a44-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="41a44-132">Bu tabloda kitaplık oluşturma amaçları için ne olacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="41a44-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="41a44-133">Seçtiğiniz .NET Standard sürümü, en yeni API 'lere erişim ve daha fazla .NET uygulaması ve .NET Standard sürümlerini hedefleyebilme arasında bir zorunluluğunu getirir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="41a44-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="41a44-134">`netstandardX.X` bir sürümünü (`X.X` bir sürüm numarası olduğu) seçerek ve proje dosyanıza (`.csproj` ya da `.fsproj`) ekleyerek hedeflenebilir platformlarının ve sürümlerinin aralığını kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="41a44-135">Gereksinimlerinize bağlı olarak .NET Standard hedeflenirken üç birincil seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="41a44-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="41a44-136">Şablonlar-`netstandard1.4` tarafından sağlanan .NET Standard varsayılan sürümünü kullanabilirsiniz. Bu, .NET Standard üzerinde API 'Lerin çoğuna, hala UWP, .NET Framework 4.6.1 ve forthverilen .NET Standard 2,0 ile uyumlu olmaya devam ederken izin verir.</span><span class="sxs-lookup"><span data-stu-id="41a44-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="41a44-137">Proje dosyanızın `TargetFramework` düğümündeki değeri değiştirerek .NET Standard daha düşük veya daha yüksek bir sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="41a44-138">.NET Standard sürümler geriye dönük olarak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="41a44-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="41a44-139">Bu, `netstandard1.0` kitaplıklarının `netstandard1.1` platformları ve daha yükseği üzerinde çalıştığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41a44-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="41a44-140">Ancak, ileri bir uyumluluk yoktur .NET Standard platformlar daha yüksek bir değere başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="41a44-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="41a44-141">Bu, `netstandard1.0` kitaplıklarının `netstandard1.1` veya üzeri hedef kitaplıklara başvurmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41a44-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="41a44-142">Gereksinimlerinize uygun API 'lerin ve platform desteğinin doğru karışımına sahip standart sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="41a44-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="41a44-143">Şimdilik `netstandard1.4` önerilir.</span><span class="sxs-lookup"><span data-stu-id="41a44-143">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="41a44-144">4,0 veya sonraki .NET Framework sürümlerini hedeflemek istiyorsanız veya .NET Standard .NET Framework (örneğin, `System.Drawing`) bir API kullanmak istiyorsanız, aşağıdaki bölümleri okuyun ve çoklu hedef hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="41a44-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="41a44-145">.NET Framework nasıl hedeflenecek</span><span class="sxs-lookup"><span data-stu-id="41a44-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="41a44-146">Bu yönergeler makinenizde .NET Framework yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="41a44-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="41a44-147">Bağımlılıkları yüklemek için [önkoşulları](#prerequisites) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="41a44-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="41a44-148">Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteğe göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="41a44-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="41a44-149">Desteklenmeyen sürümler hakkında [sss .NET Framework destek yaşam döngüsü ilkesi hakkında SSS](https://support.microsoft.com/gp/framework_faq/en-us) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41a44-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="41a44-150">En fazla geliştirici ve proje sayısına ulaşmak isterseniz, taban çizgisi hedefi olarak 4,0 .NET Framework kullanın.</span><span class="sxs-lookup"><span data-stu-id="41a44-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="41a44-151">.NET Framework hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen adını (tfd) kullanarak başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="41a44-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="41a44-152">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="41a44-152">.NET Framework version</span></span> | <span data-ttu-id="41a44-153">TFM</span><span class="sxs-lookup"><span data-stu-id="41a44-153">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="41a44-154">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="41a44-154">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="41a44-155">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="41a44-155">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="41a44-156">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="41a44-156">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="41a44-157">.NET Framework 4,0</span><span class="sxs-lookup"><span data-stu-id="41a44-157">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="41a44-158">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="41a44-158">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="41a44-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="41a44-159">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="41a44-160">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="41a44-160">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="41a44-161">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="41a44-161">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="41a44-162">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="41a44-162">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="41a44-163">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="41a44-163">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="41a44-164">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="41a44-164">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="41a44-165">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="41a44-165">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="41a44-166">Daha sonra bu tfd 'yi proje dosyanızın `TargetFramework` bölümüne eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-166">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="41a44-167">Örneğin, .NET Framework 4,0 ' i hedefleyen bir kitaplığı nasıl yazacağınız aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="41a44-167">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="41a44-168">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="41a44-168">And that's it!</span></span> <span data-ttu-id="41a44-169">Bu yalnızca .NET Framework 4 için derlense de, kitaplığı .NET Framework daha yeni sürümlerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-169">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="41a44-170">Çoklu hedef</span><span class="sxs-lookup"><span data-stu-id="41a44-170">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="41a44-171">Aşağıdaki yönergelerde .NET Framework makinenizde yüklü olduğunu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="41a44-171">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="41a44-172">Yüklemeniz gereken bağımlılıkları ve bunların nereden indirileceği hakkında bilgi edinmek için [Önkoşullar](#prerequisites) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41a44-172">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="41a44-173">Projeniz hem .NET Framework hem de .NET Core ' u desteklediğinde, .NET Framework eski sürümlerini hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-173">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="41a44-174">Bu senaryoda, daha yeni hedefler için daha yeni API 'Ler ve dil yapıları kullanmak istiyorsanız, kodunuzda `#if` yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="41a44-174">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="41a44-175">Ayrıca, hedeflediğiniz her platform için, her bir durum için gereken farklı API 'Leri dahil etmek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="41a44-175">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="41a44-176">Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="41a44-176">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="41a44-177">.NET Standard ve .NET Framework sürümleri 4,5 veya üzeri için `System.Net.Http` ad alanından `HttpClient` sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-177">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="41a44-178">Ancak, .NET Framework önceki sürümlerinde `HttpClient` sınıfı yoktur, bu nedenle `System.Net` ad alanından `WebClient` sınıfını bunun yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-178">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="41a44-179">Proje dosyanız şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="41a44-179">Your project file could look like this:</span></span>

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

<span data-ttu-id="41a44-180">Burada üç önemli değişiklik fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-180">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="41a44-181">`TargetFramework` düğümü `TargetFrameworks`ile değiştirilmiştir ve üç TFMs içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="41a44-181">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="41a44-182">`net40` hedefi için bir .NET Framework başvurusunda çekme için bir `<ItemGroup>` düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="41a44-182">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="41a44-183">İki .NET Framework başvurularında `net45` hedefi çekme için bir `<ItemGroup>` düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="41a44-183">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="41a44-184">Yapı sistemi, `#if` yönergelerinde kullanılan aşağıdaki Önişlemci sembollerinin farkındadır:</span><span class="sxs-lookup"><span data-stu-id="41a44-184">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="41a44-185">Hedefe göre koşullu derleme kullanan bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="41a44-185">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="41a44-186">Bu projeyi `dotnet build`oluşturursanız, `bin/` klasörünün altında üç dizin olduğunu fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-186">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="41a44-187">Bunların her biri, her bir hedefin `.dll` dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="41a44-187">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="41a44-188">.NET Core 'da kitaplıkları test etme</span><span class="sxs-lookup"><span data-stu-id="41a44-188">How to test libraries on .NET Core</span></span>

<span data-ttu-id="41a44-189">Platformlar arasında test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="41a44-189">It's important to be able to test across platforms.</span></span> <span data-ttu-id="41a44-190">Kutusundan [xUnit](https://xunit.github.io/) veya mstest kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-190">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="41a44-191">Her ikisi de kitaplığınızın .NET Core 'da birim testi için uygundur.</span><span class="sxs-lookup"><span data-stu-id="41a44-191">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="41a44-192">Çözümünüzü Test projeleri ile nasıl [ayarlayacağınıza çözümünüzün yapısına](#structuring-a-solution)göre değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="41a44-192">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="41a44-193">Aşağıdaki örnek, test ve kaynak dizinlerinin aynı en üst düzey dizinde canlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="41a44-193">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="41a44-194">Bu, bazı [.NET Core CLI komutlarını](../tools/index.md)kullanır.</span><span class="sxs-lookup"><span data-stu-id="41a44-194">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="41a44-195">Daha fazla bilgi için bkz. [DotNet New](../tools/dotnet-new.md) ve [DotNet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="41a44-195">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="41a44-196">Çözümünüzü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="41a44-196">Set up your solution.</span></span> <span data-ttu-id="41a44-197">Bunu aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-197">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="41a44-198">Bu, projeler oluşturur ve bunları bir çözümde birbirine bağlar.</span><span class="sxs-lookup"><span data-stu-id="41a44-198">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="41a44-199">`SolutionWithSrcAndTest` dizininiz şuna benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="41a44-199">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="41a44-200">Test projesinin dizinine gidin ve `MyProject``MyProject.Test` bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="41a44-200">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="41a44-201">Paketleri geri yükle ve projeleri oluştur:</span><span class="sxs-lookup"><span data-stu-id="41a44-201">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="41a44-202">`dotnet test` komutunu yürüterek xUnit 'nin çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="41a44-202">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="41a44-203">MSTest kullanmayı seçerseniz, bunun yerine MSTest konsol Çalıştırıcısı çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41a44-203">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="41a44-204">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="41a44-204">And that's it!</span></span> <span data-ttu-id="41a44-205">Artık, komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-205">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="41a44-206">Artık her şeyi ayarlamış olduğunuza göre teste devam etmek için, kitaplığınızı test etmek çok basittir:</span><span class="sxs-lookup"><span data-stu-id="41a44-206">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="41a44-207">Kitaplığınızda değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="41a44-207">Make changes to your library.</span></span>
1. <span data-ttu-id="41a44-208">Testleri komut satırından, test dizininizde, `dotnet test` komutuyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41a44-208">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="41a44-209">`dotnet test` komutu çağırdığınızda kodunuz otomatik olarak yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="41a44-209">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="41a44-210">Birden çok proje kullanma</span><span class="sxs-lookup"><span data-stu-id="41a44-210">How to use multiple projects</span></span>

<span data-ttu-id="41a44-211">Daha büyük kitaplıkların yaygın olması, işlevselliği farklı projelere yerleştirbir yerdir.</span><span class="sxs-lookup"><span data-stu-id="41a44-211">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="41a44-212">I, C# ve ' de tüketilen bir kitaplık oluşturmak için çok daha F#fazla düşünün.</span><span class="sxs-lookup"><span data-stu-id="41a44-212">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="41a44-213">Bu, kitaplığınızın tüketicilerinin bunları veya C# F#için doğal olan yollarla tükettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41a44-213">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="41a44-214">Örneğin, içinde C# kitaplığı şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-214">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="41a44-215">' F#De, aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="41a44-215">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="41a44-216">Buna benzer tüketim senaryoları, erişildiği API 'Lerin ve C# F#için farklı bir yapıya sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41a44-216">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="41a44-217">Bunu gerçekleştirmeye yönelik yaygın bir yaklaşım, bir kitaplığın tüm mantığını temel bir projeye, ile C# ve F# bu temel projeye çağrı yapan API katmanlarını tanımlayan projelere katmaya yönelik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="41a44-217">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="41a44-218">Bölümün geri kalanı aşağıdaki adları kullanır:</span><span class="sxs-lookup"><span data-stu-id="41a44-218">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="41a44-219">**Awesomelibrary. Core** -kitaplık için tüm mantığı içeren bir çekirdek proje</span><span class="sxs-lookup"><span data-stu-id="41a44-219">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="41a44-220">**Awesomelibrary. CSharp** -ortak API 'ler, içinde tüketim için tasarlanan bir projeC#</span><span class="sxs-lookup"><span data-stu-id="41a44-220">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="41a44-221">**Awesomelibrary. FSharp** -' de tüketim için tasarlanan ortak API 'ler içeren bir projeF#</span><span class="sxs-lookup"><span data-stu-id="41a44-221">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="41a44-222">Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-222">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="41a44-223">Bu, yukarıya üç projeyi ve bunları birbirine bağlayan bir çözüm dosyasını ekler.</span><span class="sxs-lookup"><span data-stu-id="41a44-223">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="41a44-224">Çözüm dosyası ve bağlama projeleri oluşturmak, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza olanak sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="41a44-224">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="41a44-225">Projeden projeye başvuru</span><span class="sxs-lookup"><span data-stu-id="41a44-225">Project-to-project referencing</span></span>

<span data-ttu-id="41a44-226">Bir projeye başvurmak için en iyi yöntem .NET Core CLI bir proje başvurusu eklemek için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="41a44-226">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="41a44-227">**Awesomelibrary. CSharp** ve **Awesomelibrary. FSharp** proje dizinlerinde aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-227">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="41a44-228">Hem **Awesomelibrary. CSharp** hem de **Awesomelibrary. FSharp** için proje dosyaları artık `ProjectReference` hedefi olarak **Awesomelibrary. Core** 'a başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="41a44-228">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="41a44-229">Bunu, proje dosyalarını inceleyerek ve içinde aşağıdakileri görerek doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a44-229">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="41a44-230">.NET Core CLI kullanmayı tercih ediyorsanız, bu bölümü her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a44-230">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="41a44-231">Çözüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="41a44-231">Structuring a solution</span></span>

<span data-ttu-id="41a44-232">Çok projeli çözümlerin diğer önemli bir yönü de iyi bir genel proje yapısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="41a44-232">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="41a44-233">İsterseniz kodu düzenleyebilir ve her bir projeyi `dotnet sln add`çözüm dosyanıza bağladığınızda, çözüm düzeyinde `dotnet restore` ve `dotnet build` çalıştırabileceksiniz demektir.</span><span class="sxs-lookup"><span data-stu-id="41a44-233">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
