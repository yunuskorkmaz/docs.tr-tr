---
title: .NET Core CLI ile kütüphaneler geliştirin
description: .NET Core CLI'yi kullanarak .NET Core kitaplıklarını nasıl oluşturabilirsiniz öğrenin. Birden çok çerçeveyi destekleyen bir kitaplık oluşturursunuz.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503502"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="76d83-104">.NET Core CLI ile kütüphaneler geliştirin</span><span class="sxs-lookup"><span data-stu-id="76d83-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="76d83-105">Bu makalede,.NET CLI'yi kullanarak .NET için kitaplıkların nasıl yazılalıyorum.</span><span class="sxs-lookup"><span data-stu-id="76d83-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="76d83-106">CLI, desteklenen tüm işletim sistemi genelinde çalışan verimli ve düşük seviyeli bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="76d83-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="76d83-107">Visual Studio ile kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim buysa [Visual Studio kılavuzuna bakın.](library-with-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="76d83-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76d83-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="76d83-108">Prerequisites</span></span>

<span data-ttu-id="76d83-109">Makinenize [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) yüklü olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="76d83-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="76d83-110">Bu belgenin .NET Framework sürümleriyle ilgili bölümleri için bir Windows makinesine yüklü [.NET Framework](https://dotnet.microsoft.com) gerekir.</span><span class="sxs-lookup"><span data-stu-id="76d83-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="76d83-111">Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.NET indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)hedefleme paketleri veya geliştirici paketleri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="76d83-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="76d83-112">Bu tabloya bakın:</span><span class="sxs-lookup"><span data-stu-id="76d83-112">Refer to this table:</span></span>

| <span data-ttu-id="76d83-113">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="76d83-113">.NET Framework version</span></span> | <span data-ttu-id="76d83-114">Ne indirmek için</span><span class="sxs-lookup"><span data-stu-id="76d83-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="76d83-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="76d83-115">4.6.1</span></span>                  | <span data-ttu-id="76d83-116">.NET Framework 4.6.1 Hedefleme Paketi</span><span class="sxs-lookup"><span data-stu-id="76d83-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="76d83-117">4.6</span><span class="sxs-lookup"><span data-stu-id="76d83-117">4.6</span></span>                    | <span data-ttu-id="76d83-118">.NET Framework 4.6 Hedefleme Paketi</span><span class="sxs-lookup"><span data-stu-id="76d83-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="76d83-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="76d83-119">4.5.2</span></span>                  | <span data-ttu-id="76d83-120">.NET Framework 4.5.2 Geliştirici Paketi</span><span class="sxs-lookup"><span data-stu-id="76d83-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="76d83-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="76d83-121">4.5.1</span></span>                  | <span data-ttu-id="76d83-122">.NET Framework 4.5.1 Geliştirici Paketi</span><span class="sxs-lookup"><span data-stu-id="76d83-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="76d83-123">4,5</span><span class="sxs-lookup"><span data-stu-id="76d83-123">4.5</span></span>                    | <span data-ttu-id="76d83-124">Windows 8 için Windows Yazılım Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="76d83-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="76d83-125">4.0</span><span class="sxs-lookup"><span data-stu-id="76d83-125">4.0</span></span>                    | <span data-ttu-id="76d83-126">Windows 7 için Windows SDK ve .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="76d83-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="76d83-127">2.0, 3.0 ve 3.5</span><span class="sxs-lookup"><span data-stu-id="76d83-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="76d83-128">.NET Framework 3.5 SP1 Çalışma Süresi (veya Windows 8+ sürümü)</span><span class="sxs-lookup"><span data-stu-id="76d83-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="76d83-129">.NET Standardı nasıl hedefilir?</span><span class="sxs-lookup"><span data-stu-id="76d83-129">How to target the .NET Standard</span></span>

<span data-ttu-id="76d83-130">.NET Standard'ı bilmiyorsanız, daha fazla bilgi edinmek için [.NET Standard'a](../../standard/net-standard.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="76d83-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="76d83-131">Bu makalede, .NET Standart sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:</span><span class="sxs-lookup"><span data-stu-id="76d83-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="76d83-132">Bu tablo, kitaplık oluşturmak amacıyla şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="76d83-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="76d83-133">Seçtiğiniz .NET Standard sürümü, en yeni API'lere erişim ile daha fazla .NET uygulaması ve .NET Standart sürümlerini hedefleme olanağı arasında bir denge olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76d83-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="76d83-134">Hedeflenen platformların ve sürümlerin `netstandardX.X` aralığını bir sürümünü `X.X` seçerek (sürüm numarası nın bulunduğu yer) `.fsproj`ve proje dosyanıza (veya)`.csproj` ekleyerek denetlersiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="76d83-135">İhtiyaçlarınıza bağlı olarak .NET Standard'ı hedef alırken üç ana seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="76d83-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="76d83-136">UWP, `netstandard1.4`.NET Framework 4.6.1 ve .NET Standard 2.0 ile uyumlu yken .NET Standardı'ndaki çoğu API'ye erişmenizi sağlayan şablonlar tarafından sağlanan .NET Standard'ın varsayılan sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="76d83-137">Proje dosyanızın `TargetFramework` düğümündeki değeri değiştirerek .NET Standard'ın daha düşük veya daha yüksek bir sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="76d83-138">.NET Standart sürümleri geriye dönük uyumludur.</span><span class="sxs-lookup"><span data-stu-id="76d83-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="76d83-139">Bu, `netstandard1.0` kitaplıkların `netstandard1.1` platformlarda ve daha yüksek platformlarda çalıştırıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76d83-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="76d83-140">Ancak, ileri uyumluluk yoktur.</span><span class="sxs-lookup"><span data-stu-id="76d83-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="76d83-141">Alt .NET Standart platformlar daha yüksek platformlara başvuruyapamaz.</span><span class="sxs-lookup"><span data-stu-id="76d83-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="76d83-142">Bu, `netstandard1.0` kitaplıkların hedefleme `netstandard1.1` veya daha yüksek kitaplıkları referans veremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76d83-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="76d83-143">İhtiyaçlarınız için DOĞRU API ve platform desteği karışımına sahip Standart sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="76d83-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="76d83-144">Şimdilik `netstandard1.4` tavsiye ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="76d83-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="76d83-145">.NET Framework sürümleri4.0 veya altında hedeflemek istiyorsanız veya .NET Framework'de bulunan ancak .NET Standard'da `System.Drawing`(örneğin) bulunmayan bir API kullanmak istiyorsanız, aşağıdaki bölümleri okuyun ve nasıl çoklu hedef le hedeflenmeyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="76d83-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="76d83-146">.NET Framework nasıl hedefilir?</span><span class="sxs-lookup"><span data-stu-id="76d83-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="76d83-147">Bu talimatlar makinenizde .NET Framework yüklü olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="76d83-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="76d83-148">Bağımlılıkları yüklemek için [Ön koşullara](#prerequisites) bakın.</span><span class="sxs-lookup"><span data-stu-id="76d83-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="76d83-149">Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76d83-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="76d83-150">Desteklenmeyen sürümler hakkında [.NET Framework Support Yaşam Döngüsü İlkesi SSS'sine](https://support.microsoft.com/gp/framework_faq/en-us) bakın.</span><span class="sxs-lookup"><span data-stu-id="76d83-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="76d83-151">Maksimum geliştirici ve proje sayısına ulaşmak istiyorsanız, temel hedefiniz olarak .NET Framework 4.0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="76d83-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="76d83-152">.NET Framework'ü hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru Hedef Çerçeve Takma Adı (TFM) kullanarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="76d83-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="76d83-153">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="76d83-153">.NET Framework version</span></span> | <span data-ttu-id="76d83-154">Tfm</span><span class="sxs-lookup"><span data-stu-id="76d83-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="76d83-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="76d83-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="76d83-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="76d83-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="76d83-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="76d83-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="76d83-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="76d83-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="76d83-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="76d83-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="76d83-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="76d83-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="76d83-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="76d83-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="76d83-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="76d83-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="76d83-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="76d83-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="76d83-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="76d83-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="76d83-165"> .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="76d83-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="76d83-166"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="76d83-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="76d83-167">Daha sonra bu TFM'yi proje dosyanızın bölümüne `TargetFramework` eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="76d83-168">Örneğin, .NET Framework 4.0'ı hedefleyen bir kitaplığı şu şekilde yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="76d83-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="76d83-169">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="76d83-169">And that's it!</span></span> <span data-ttu-id="76d83-170">Bu yalnızca .NET Framework 4 için derlenmiş olsa da, .NET Framework'ün yeni sürümlerinde kitaplığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="76d83-171">Çoklu hedef nasıl</span><span class="sxs-lookup"><span data-stu-id="76d83-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="76d83-172">Aşağıdaki talimatlar makinenizde .NET Framework yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="76d83-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="76d83-173">Hangi bağımlılıkları yüklemeniz gerektiğini ve bunları nereden indirmeniz gerektiğini öğrenmek için [Önkoşullar](#prerequisites) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="76d83-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="76d83-174">Projeniz hem .NET Framework'ü hem de .NET Core'u desteklediğinde .NET Framework'ün eski sürümlerini hedeflemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="76d83-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="76d83-175">Bu senaryoda, yeni hedefler için daha yeni API'ler ve dil `#if` yapıları kullanmak istiyorsanız, kodunuzda yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="76d83-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="76d83-176">Ayrıca, hedeflediğiniz her platform için her servis talebi için gereken farklı API'leri eklemek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="76d83-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="76d83-177">Örneğin, http üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="76d83-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="76d83-178">.NET Standard ve .NET Framework sürümleri 4.5 veya `HttpClient` üzeri için `System.Net.Http` sınıfı ad alanından kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="76d83-179">Ancak, .NET Framework'ün önceki sürümlerinde `HttpClient` sınıf yoktur, bu `WebClient` nedenle `System.Net` sınıfı ad alanından kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="76d83-180">Proje dosyanız şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="76d83-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="76d83-181">Burada üç büyük değişiklik fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="76d83-182">Düğüm `TargetFramework` , `TargetFrameworks`ve üç TFMs içinde ifade edilmiştir değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="76d83-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="76d83-183">Bir .NET Framework `<ItemGroup>` `net40` referansını çeken hedef için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="76d83-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="76d83-184">İki .NET Framework `<ItemGroup>` `net45` referansı çeken hedef için bir düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="76d83-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="76d83-185">Yapı sistemi, direktiflerde `#if` kullanılan aşağıdaki önişlemci sembollerinden haberdardır:</span><span class="sxs-lookup"><span data-stu-id="76d83-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="76d83-186">Aşağıda, hedef başına koşullu derlemeden yararlanılanbir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="76d83-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="76d83-187">Bu projeyi klasörün `dotnet build` `bin/` altında üç dizin le oluşturursanız:</span><span class="sxs-lookup"><span data-stu-id="76d83-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="76d83-188">Bunların her biri, her hedef için `.dll` dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="76d83-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="76d83-189">.NET Core'da kitaplıklar nasıl test edilebilir?</span><span class="sxs-lookup"><span data-stu-id="76d83-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="76d83-190">Platformlar arasında test edebilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76d83-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="76d83-191">[XUnit](https://xunit.github.io/) veya MSTest'i kutunun dışında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="76d83-192">Her ikisi de .NET Core'da kitaplığınızı test etmek için mükemmel bir şekilde uygundur.</span><span class="sxs-lookup"><span data-stu-id="76d83-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="76d83-193">Çözümünüzü test projeleri ile nasıl ayarlayacağınız [çözümünuzun yapısına](#structuring-a-solution)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="76d83-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="76d83-194">Aşağıdaki örnek, test ve kaynak dizinlerinin aynı üst düzey dizinde yaşadığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="76d83-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="76d83-195">Bu bazı [.NET Core CLI](../tools/index.md) komutları kullanır.</span><span class="sxs-lookup"><span data-stu-id="76d83-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="76d83-196">Daha fazla bilgi için [dotnet yeni](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="76d83-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="76d83-197">Çözümünüzü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76d83-197">Set up your solution.</span></span> <span data-ttu-id="76d83-198">Bunu aşağıdaki komutlarla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="76d83-199">Bu projeler oluşturmak ve bir çözüm onları birbirine bağlayacak.</span><span class="sxs-lookup"><span data-stu-id="76d83-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="76d83-200">Dizin için `SolutionWithSrcAndTest` bu gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="76d83-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="76d83-201">Test projesinin dizinine gidin ve `MyProject.Test` 'den `MyProject`bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="76d83-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="76d83-202">Paketleri geri yükleyin ve projeler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="76d83-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="76d83-203">`dotnet test` xUnit'in komutu çalıştırarak çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="76d83-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="76d83-204">MSTest'i kullanmayı seçtiyseniz, bunun yerine MSTest konsol koşucusu çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76d83-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="76d83-205">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="76d83-205">And that's it!</span></span> <span data-ttu-id="76d83-206">Artık komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="76d83-207">Her şeyi ayarladığınızdasına göre sınamalara devam etmek için kitaplığınızı test etmek çok basittir:</span><span class="sxs-lookup"><span data-stu-id="76d83-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="76d83-208">Kitaplığınızda değişiklik yapın.</span><span class="sxs-lookup"><span data-stu-id="76d83-208">Make changes to your library.</span></span>
1. <span data-ttu-id="76d83-209">Komut satırından, test dizininizde komutla `dotnet test` testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="76d83-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="76d83-210">Komutu çağırdığınızda `dotnet test` kodunuz otomatik olarak yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76d83-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="76d83-211">Birden çok proje nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="76d83-211">How to use multiple projects</span></span>

<span data-ttu-id="76d83-212">Daha büyük kitaplıklar için ortak bir ihtiyaç farklı projelerde işlevsellik yerleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="76d83-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="76d83-213">Deyimsel C# ve F# olarak tüketilebilen bir kütüphane oluşturmak istediğinizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="76d83-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="76d83-214">Bu, kitaplığınızın tüketicilerinin bu kitabı C# veya F# açısından doğal şekillerde tükettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76d83-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="76d83-215">Örneğin, C# kitaplığını şu şekilde tüketebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="76d83-216">F#'da şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="76d83-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="76d83-217">Bu gibi tüketim senaryoları, erişilen API'lerin C# ve F# için farklı bir yapıya sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76d83-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="76d83-218">Bunu gerçekleştirmek için ortak bir yaklaşım, bir kitaplığın tüm mantığını, c# ve F# projeleri ile bu temel projeye çağrı yapan API katmanlarını tanımlayan bir çekirdek projeye dahil etmektir.</span><span class="sxs-lookup"><span data-stu-id="76d83-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="76d83-219">Bölümün geri kalanı aşağıdaki adları kullanır:</span><span class="sxs-lookup"><span data-stu-id="76d83-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="76d83-220">**AwesomeLibrary.Core** - kütüphane için tüm mantığı içeren bir çekirdek proje</span><span class="sxs-lookup"><span data-stu-id="76d83-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="76d83-221">**AwesomeLibrary.CSharp** - C tüketimi için tasarlanmış kamu API'leri ile bir proje #</span><span class="sxs-lookup"><span data-stu-id="76d83-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="76d83-222">**AwesomeLibrary.FSharp** - F tüketimi için tasarlanmış kamu API'leri ile bir proje #</span><span class="sxs-lookup"><span data-stu-id="76d83-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="76d83-223">Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="76d83-224">Bu, yukarıdaki üç projeyi ve onları birbirine bağlayan bir çözüm dosyasını ekler.</span><span class="sxs-lookup"><span data-stu-id="76d83-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="76d83-225">Çözüm dosyası oluşturma ve projeleri bağlama, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76d83-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="76d83-226">Projeden projeye başvuru</span><span class="sxs-lookup"><span data-stu-id="76d83-226">Project-to-project referencing</span></span>

<span data-ttu-id="76d83-227">Bir projeye başvurmanın en iyi yolu, bir proje başvurusu eklemek için .NET Core CLI'yi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="76d83-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="76d83-228">**AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinleri, aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="76d83-229">**Hem AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** için proje dosyaları şimdi bir `ProjectReference` hedef olarak **AwesomeLibrary.Core** başvuruolacaktır.</span><span class="sxs-lookup"><span data-stu-id="76d83-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="76d83-230">Proje dosyalarını inceleyerek ve aşağıdakileri görerek bunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76d83-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="76d83-231">.NET Core CLI'yi kullanmamak isterseniz bu bölümü her proje dosyasına el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d83-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="76d83-232">Çözüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76d83-232">Structuring a solution</span></span>

<span data-ttu-id="76d83-233">Çok projeli çözümlerin bir diğer önemli yönü de iyi bir genel proje yapısı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="76d83-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="76d83-234">Kodu istediğiniz gibi düzenleyebilirsiniz ve her projeyi çözüm dosyanıza `dotnet sln add`bağladiğiniz sürece, `dotnet restore` çalıştırabilirsiniz ve `dotnet build` çözüm düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="76d83-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
