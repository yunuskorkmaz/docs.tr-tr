---
title: .NET 5 ' teki yenilikler
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 9d4fc514c9de7a668f909286f10d6fe28ada7f90
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955206"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="c5ff5-103">.NET 5 ' teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="c5ff5-103">What's new in .NET 5</span></span>

<span data-ttu-id="c5ff5-104">.NET Core, .NET Core 'un gelişmidir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-104">.NET 5 is the evolution of .NET Core.</span></span> <span data-ttu-id="c5ff5-105">Bu makalede, .NET Core 'un sonraki sürümü olan 3,1 ' de bulunan .NET 5 ' te yer alan ayrıntılar ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-105">This article details what's included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="c5ff5-106">Sürüm numarası, .NET Framework 4. x ile karışıklık oluşmasını önlemek için 5,0.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-106">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="c5ff5-107">Ve "çekirdek", .NET ' in ana uygulama olduğu için adından bırakılır.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-107">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="c5ff5-108">ASP.NET Core, ASP.NET MVC 5 ile karıştırmamak için "Core" adını korur.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-108">ASP.NET Core retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="c5ff5-109">Ayrıca, Entity Framework Core "çekirdek" adını Entity Framework 5 ve 6 ile karıştırmamak için korur.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-109">Additionally, Entity Framework Core retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span> <span data-ttu-id="c5ff5-110">.NET 5, .NET Core veya .NET Framework daha fazla sayıda uygulamayı ve daha fazlasını destekler.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-110">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="c5ff5-111">.NET Core 'un bir bütün olarak .NET ekosistemini etkileyici yollarla geliştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-111">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="c5ff5-112">GitHub 'da açık kaynaklı bir proje olarak, topluluk katkılarını kutluyor ve zaman içinde gelişerek daha fazla iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-112">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="c5ff5-113">.NET Core 'un birkaç birincil özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-113">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c5ff5-114">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="c5ff5-114">Cross-platform</span></span>
> - <span data-ttu-id="c5ff5-115">Açık kaynak</span><span class="sxs-lookup"><span data-stu-id="c5ff5-115">Open-source</span></span>
> - <span data-ttu-id="c5ff5-116">Yan yana yükleme</span><span class="sxs-lookup"><span data-stu-id="c5ff5-116">Side-by-side installation</span></span>
> - <span data-ttu-id="c5ff5-117">Küçük proje dosyaları (SDK stili)</span><span class="sxs-lookup"><span data-stu-id="c5ff5-117">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="c5ff5-118">Esnek dağıtım</span><span class="sxs-lookup"><span data-stu-id="c5ff5-118">Flexible deployment</span></span>

<span data-ttu-id="c5ff5-119">.NET 5 bu özellikleri genişleterek artımlı iyileştirmeler yapar:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-119">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="c5ff5-120">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c5ff5-120">Single file apps</span></span>
- <span data-ttu-id="c5ff5-121">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-121">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="c5ff5-122">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-122">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="c5ff5-123">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="c5ff5-123">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="c5ff5-124">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c5ff5-124">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="c5ff5-125">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="c5ff5-125">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="c5ff5-126">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="c5ff5-126">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="c5ff5-127">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="c5ff5-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="c5ff5-128">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-128">Container size optimizations</span></span>
- [<span data-ttu-id="c5ff5-129">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="c5ff5-129">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="c5ff5-130">C# derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-130">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="c5ff5-131">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="c5ff5-131">Tooling support for dump debugging</span></span>
- <span data-ttu-id="c5ff5-132">Platform [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için %80 açıklanmalıdır</span><span class="sxs-lookup"><span data-stu-id="c5ff5-132">Platform is 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="c5ff5-133">.NET 5 ne değildir?</span><span class="sxs-lookup"><span data-stu-id="c5ff5-133">What .NET 5 is not</span></span>

<span data-ttu-id="c5ff5-134">.NET 5 .NET Framework için tamamen değişiklik değildir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-134">.NET 5 is not a complete replacement for .NET Framework.</span></span> <span data-ttu-id="c5ff5-135">Aşağıdaki teknolojilerin .NET Framework .NET 5 ' e bağlantı noktası yoktur, ancak desteklenen alternatifler vardır:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-135">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives:</span></span>

| <span data-ttu-id="c5ff5-136">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="c5ff5-136">Technology</span></span>                             | <span data-ttu-id="c5ff5-137">Önerilen alternatif</span><span class="sxs-lookup"><span data-stu-id="c5ff5-137">Recommended alternative</span></span>                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c5ff5-138">Web Forms</span><span class="sxs-lookup"><span data-stu-id="c5ff5-138">Web Forms</span></span>                              | <span data-ttu-id="c5ff5-139">ASP.NET Core [Blazor](/aspnet/core/blazor) veya [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="c5ff5-139">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="c5ff5-140">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c5ff5-140">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="c5ff5-141">gRPC</span><span class="sxs-lookup"><span data-stu-id="c5ff5-141">gRPC</span></span>](/aspnet/core/grpc)                                                                       |
| <span data-ttu-id="c5ff5-142">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="c5ff5-142">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="c5ff5-143">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="c5ff5-143">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

## <a name="net-standard"></a><span data-ttu-id="c5ff5-144">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c5ff5-144">.NET Standard</span></span>

<span data-ttu-id="c5ff5-145">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-145">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="c5ff5-146">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-146">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="c5ff5-147">`net5.0`Tfd, ve adlarını birleştirir ve `netcoreapp` değiştirir `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-147">The `net5.0` TFM combines and replaces the `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="c5ff5-148">Bu TFM genellikle, .NET Standard gibi, platformlar arası çalışan teknolojileri dahil eder.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-148">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="c5ff5-149">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-149">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="c5ff5-150">Daha fazla bilgi için bkz. [hedef çerçeveleri belirtme](../standard/frameworks.md#how-to-specify-a-target-framework).</span><span class="sxs-lookup"><span data-stu-id="c5ff5-150">For more information, see [How to specify target frameworks](../standard/frameworks.md#how-to-specify-a-target-framework).</span></span>

## <a name="language-updates"></a><span data-ttu-id="c5ff5-151">Dil güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-151">Language updates</span></span>

<span data-ttu-id="c5ff5-152">.NET 5 ile .NET programlama dilleri iyileştirilmesine devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-152">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="c5ff5-153">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-153">C# updates</span></span>

<span data-ttu-id="c5ff5-154">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-154">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="c5ff5-155">.NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-155">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="c5ff5-156">Aşağıda bazı önemli noktalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-156">Here are a few highlights:</span></span>

- <span data-ttu-id="c5ff5-157">Kayıtlar: değer türleri gibi davranan ve yeni anahtar sözcüğünü dile tanıtan değişmez başvuru türleri `with` .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-157">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="c5ff5-158">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-158">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="c5ff5-159">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-159">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="c5ff5-160">İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-160">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="c5ff5-161">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-161">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="c5ff5-162">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="c5ff5-162">Source generators</span></span>

<span data-ttu-id="c5ff5-163">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-163">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="c5ff5-164">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-164">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="c5ff5-165">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-165">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="c5ff5-166">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5ff5-166">F# updates</span></span>

<span data-ttu-id="c5ff5-167">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-167">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="c5ff5-168">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-168">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="c5ff5-169">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="c5ff5-169">Interpolated strings</span></span>

<span data-ttu-id="c5ff5-170">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript, F # temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-170">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="c5ff5-171">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-171">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="c5ff5-172">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-172">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="c5ff5-173">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-173">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a><span data-ttu-id="c5ff5-174">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-174">Visual Basic updates</span></span>

<span data-ttu-id="c5ff5-175">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-175">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="c5ff5-176">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-176">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="c5ff5-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5ff5-177">Description</span></span>                            | <span data-ttu-id="c5ff5-178">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="c5ff5-178">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="c5ff5-179">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="c5ff5-179">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="c5ff5-180">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-180">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="c5ff5-181">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="c5ff5-181">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="c5ff5-182">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-182">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="c5ff5-183">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-183">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="c5ff5-184">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-184">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="c5ff5-185">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="c5ff5-185">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="c5ff5-186">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-186">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="c5ff5-187">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="c5ff5-187">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="c5ff5-188">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="c5ff5-188">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="c5ff5-189">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="c5ff5-189">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="c5ff5-190">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="c5ff5-190">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="c5ff5-191">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="c5ff5-191">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="c5ff5-192">.NET MAUı</span><span class="sxs-lookup"><span data-stu-id="c5ff5-192">.NET MAUI</span></span>

<span data-ttu-id="c5ff5-193">.NET MAUı, giderek daha popüler Xamarin. Forms araç seti 'nin bir evrimi ve [DotNet/MAUI](https://github.com/dotnet/maui)'de GitHub 'da açık kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-193">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="c5ff5-194">.Net MAUı sayesinde, .NET geliştiricileri için seçim, tüm modern iş yüklerini destekleyen tek bir yığın sağlayan basitleştirilmiştir: Android, iOS, macOS ve Windows.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-194">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="c5ff5-195">.NET MAUı ile birden çok platformu ve cihazı hedefleyen tek bir proje geliştirici deneyimi edinirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-195">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5ff5-196">.NET MAUı erken önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-196">.NET MAUI is in early preview.</span></span> <span data-ttu-id="c5ff5-197">Örnek kaynak kodu, [Xamarin/NET6-Samples](https://github.com/xamarin/net6-samples)adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-197">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="c5ff5-198">Model-Görünüm-güncelleştirme modeli</span><span class="sxs-lookup"><span data-stu-id="c5ff5-198">Model-View-Update pattern</span></span>

<span data-ttu-id="c5ff5-199">Geliştiriciler modern geliştirme düzenlerini sevdiğinde.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-199">Developers love modern development patterns.</span></span> <span data-ttu-id="c5ff5-200">UI geliştirmeye yönelik akıcı bir yaklaşım, "karaağaç mimarisi" tarafından ilham [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) veya MVU deseninin bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-200">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="c5ff5-201">MVU veri ve durum yönetiminin tek yönlü bir akışını ve yalnızca gerekli değişiklikleri uygulayarak Kullanıcı arabirimini hızla güncelleştiren bir kod ilk geliştirme deneyimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-201">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="c5ff5-202">Örnek olarak, MVU modelini kullanarak .NET MAUı 'de yazılmış aşağıdaki sayacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c5ff5-202">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

<span data-ttu-id="c5ff5-203">Daha fazla bilgi için bkz. [.net MAUI yol haritası](https://github.com/dotnet/maui/wiki/Roadmap)ve [.net MAUI makalesine giriş](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="c5ff5-203">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5ff5-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5ff5-204">See also</span></span>

- [<span data-ttu-id="c5ff5-205">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="c5ff5-205">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="c5ff5-206">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c5ff5-206">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
