---
title: .NET Core 'un .NET 5 sürümüne evrimi
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 5e8ed371173ff8b81909ceb071ed93c6b0e1eea5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515845"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="c9620-103">.NET Core 'un .NET 5 sürümüne evrimi</span><span class="sxs-lookup"><span data-stu-id="c9620-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="c9620-104">Bu makalede, .NET Core 'un sonraki sürümü olan 3,1 ' de bulunan .NET 5 ' te nelerin dahil olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c9620-104">This article details what is included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="c9620-105">Sürüm numarası, .NET Framework 4. x ile karışıklık oluşmasını önlemek için 5,0.</span><span class="sxs-lookup"><span data-stu-id="c9620-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="c9620-106">Ve "çekirdek", .NET ' in ana uygulama olduğu için adından bırakılır.</span><span class="sxs-lookup"><span data-stu-id="c9620-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="c9620-107">ASP.NET Core, ASP.NET MVC 5 ile karıştırmamak için "Core" adını korur.</span><span class="sxs-lookup"><span data-stu-id="c9620-107">ASP.NET Core retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="c9620-108">Ayrıca, Entity Framework Core "çekirdek" adını Entity Framework 5 ve 6 ile karıştırmamak için korur.</span><span class="sxs-lookup"><span data-stu-id="c9620-108">Additionally, Entity Framework Core retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span> <span data-ttu-id="c9620-109">.NET 5, .NET Core veya .NET Framework daha fazla sayıda uygulamayı ve daha fazlasını destekler.</span><span class="sxs-lookup"><span data-stu-id="c9620-109">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="c9620-110">.NET Core 'un bir bütün olarak .NET ekosistemini etkileyici yollarla geliştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="c9620-110">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="c9620-111">GitHub 'da açık kaynaklı bir proje olarak, topluluk katkılarını kutluyor ve zaman içinde gelişerek daha fazla iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="c9620-111">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="c9620-112">.NET Core 'un birkaç birincil özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="c9620-112">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c9620-113">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="c9620-113">Cross-platform</span></span>
> - <span data-ttu-id="c9620-114">Açık kaynak</span><span class="sxs-lookup"><span data-stu-id="c9620-114">Open-source</span></span>
> - <span data-ttu-id="c9620-115">Yan yana yükleme</span><span class="sxs-lookup"><span data-stu-id="c9620-115">Side-by-side installation</span></span>
> - <span data-ttu-id="c9620-116">Küçük proje dosyaları (SDK stili)</span><span class="sxs-lookup"><span data-stu-id="c9620-116">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="c9620-117">Esnek dağıtım</span><span class="sxs-lookup"><span data-stu-id="c9620-117">Flexible deployment</span></span>

<span data-ttu-id="c9620-118">.NET 5 bu özellikleri genişleterek artımlı iyileştirmeler yapar:</span><span class="sxs-lookup"><span data-stu-id="c9620-118">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="c9620-119">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c9620-119">Single file apps</span></span>
- <span data-ttu-id="c9620-120">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="c9620-120">Windows ARM64, and ARM64 intrinsics</span></span>
- <span data-ttu-id="c9620-121">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="c9620-121">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="c9620-122">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="c9620-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="c9620-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c9620-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="c9620-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="c9620-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="c9620-125">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="c9620-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="c9620-126">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="c9620-126">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="c9620-127">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-127">Container size optimizations</span></span>
- [<span data-ttu-id="c9620-128">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="c9620-128">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="c9620-129">C# derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-129">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="c9620-130">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="c9620-130">Tooling support for dump debugging</span></span>
- <span data-ttu-id="c9620-131">Platform [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için %80 açıklanmalıdır</span><span class="sxs-lookup"><span data-stu-id="c9620-131">Platform is 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="c9620-132">.NET 5 ne değildir?</span><span class="sxs-lookup"><span data-stu-id="c9620-132">What .NET 5 is not</span></span>

<span data-ttu-id="c9620-133">.NET 5 .NET Framework için bir değiştirme değildir.</span><span class="sxs-lookup"><span data-stu-id="c9620-133">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="c9620-134">Aşağıdaki teknolojilerin .NET Framework .NET 5 ' e bağlantı noktası yoktur, ancak .NET 5 ' te desteklenen alternatifler bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="c9620-134">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="c9620-135">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="c9620-135">Technology</span></span>                             | <span data-ttu-id="c9620-136">Öneri</span><span class="sxs-lookup"><span data-stu-id="c9620-136">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="c9620-137">Web Forms</span><span class="sxs-lookup"><span data-stu-id="c9620-137">Web Forms</span></span>                              | [<span data-ttu-id="c9620-138">ASP.NET Core Blazor</span><span class="sxs-lookup"><span data-stu-id="c9620-138">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="c9620-139">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c9620-139">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="c9620-140">gRPC</span><span class="sxs-lookup"><span data-stu-id="c9620-140">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="c9620-141">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="c9620-141">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="c9620-142">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="c9620-142">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="c9620-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c9620-143">.NET Standard</span></span>

<span data-ttu-id="c9620-144">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c9620-144">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="c9620-145">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="c9620-145">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="c9620-146">`net5.0`Tfd, ve adlarını birleştirir ve değiştirir `netcoreapp` `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="c9620-146">The `net5.0` TFM combines and replaces `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="c9620-147">Bu TFM genellikle, .NET Standard gibi, platformlar arası çalışan teknolojileri dahil eder.</span><span class="sxs-lookup"><span data-stu-id="c9620-147">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="c9620-148">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9620-148">However, if you're planning on sharing code between .NET Framework, .NET Core, and .NET 5 workloads - you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="c9620-149">Daha fazla bilgi için bkz. [hedef çerçeveleri belirtme](../standard/frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="c9620-149">For more information, see [How to specify target frameworks](../standard/frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="language-updates"></a><span data-ttu-id="c9620-150">Dil güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-150">Language updates</span></span>

<span data-ttu-id="c9620-151">.NET 5 ile .NET programlama dilleri iyileştirilmesine devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9620-151">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="c9620-152">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-152">C# updates</span></span>

<span data-ttu-id="c9620-153">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="c9620-153">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="c9620-154">.NET 5, C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c9620-154">.NET 5 is paired with C# 9.</span></span> <span data-ttu-id="c9620-155">C# 9, dile birçok yeni özellik getirir, bazı önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c9620-155">C# 9 brings many new features to the language, here are a few highlights:</span></span>

- <span data-ttu-id="c9620-156">Kayıtlar: değer türleri gibi davranan ve yeni anahtar sözcüğünü dile tanıtan değişmez başvuru türleri `with` .</span><span class="sxs-lookup"><span data-stu-id="c9620-156">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="c9620-157">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="c9620-157">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="c9620-158">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="c9620-158">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="c9620-159">İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="c9620-159">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="c9620-160">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="c9620-160">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="c9620-161">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="c9620-161">Source generators</span></span>

<span data-ttu-id="c9620-162">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="c9620-162">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="c9620-163">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c9620-163">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="c9620-164">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="c9620-164">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="c9620-165">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c9620-165">F# updates</span></span>

<span data-ttu-id="c9620-166">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="c9620-166">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="c9620-167">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c9620-167">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="c9620-168">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="c9620-168">Interpolated strings</span></span>

<span data-ttu-id="c9620-169">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript-F #, temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="c9620-169">Similar to interpolated string in C#, and even JavaScript - F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="c9620-170">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="c9620-170">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="c9620-171">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9620-171">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="c9620-172">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c9620-172">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a><span data-ttu-id="c9620-173">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-173">Visual Basic updates</span></span>

<span data-ttu-id="c9620-174">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="c9620-174">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="c9620-175">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="c9620-175">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="c9620-176">Description</span><span class="sxs-lookup"><span data-stu-id="c9620-176">Description</span></span>                            | <span data-ttu-id="c9620-177">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="c9620-177">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="c9620-178">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="c9620-178">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="c9620-179">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c9620-179">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="c9620-180">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="c9620-180">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="c9620-181">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c9620-181">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="c9620-182">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c9620-182">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="c9620-183">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c9620-183">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="c9620-184">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="c9620-184">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="c9620-185">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c9620-185">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="c9620-186">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="c9620-186">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="c9620-187">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="c9620-187">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="c9620-188">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="c9620-188">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="c9620-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="c9620-189">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="c9620-190">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="c9620-190">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="c9620-191">.NET MAUı</span><span class="sxs-lookup"><span data-stu-id="c9620-191">.NET MAUI</span></span>

<span data-ttu-id="c9620-192">.NET MAUı, giderek daha popüler Xamarin. Forms araç seti 'nin bir evrimi ve [DotNet/MAUI](https://github.com/dotnet/maui)'de GitHub 'da açık kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="c9620-192">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="c9620-193">.Net MAUı sayesinde, .NET geliştiricileri için seçim, tüm modern iş yüklerini destekleyen tek bir yığın sağlayan basitleştirilmiştir: Android, iOS, macOS ve Windows.</span><span class="sxs-lookup"><span data-stu-id="c9620-193">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="c9620-194">.NET MAUı ile birden çok platformu ve cihazı hedefleyen tek bir proje geliştirici deneyimi edinirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9620-194">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9620-195">.NET MAUı erken önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="c9620-195">.NET MAUI is in early preview.</span></span> <span data-ttu-id="c9620-196">Örnek kaynak kodu, [Xamarin/NET6-Samples](https://github.com/xamarin/net6-samples)adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c9620-196">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="c9620-197">Model-Görünüm-güncelleştirme modeli</span><span class="sxs-lookup"><span data-stu-id="c9620-197">Model-View-Update pattern</span></span>

<span data-ttu-id="c9620-198">Geliştiriciler modern geliştirme düzenlerini sevdiğinde.</span><span class="sxs-lookup"><span data-stu-id="c9620-198">Developers love modern development patterns.</span></span> <span data-ttu-id="c9620-199">UI geliştirmeye yönelik akıcı bir yaklaşım, "karaağaç mimarisi" tarafından ilham [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) veya MVU deseninin bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c9620-199">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="c9620-200">MVU veri ve durum yönetiminin tek yönlü bir akışını ve yalnızca gerekli değişiklikleri uygulayarak Kullanıcı arabirimini hızla güncelleştiren bir kod ilk geliştirme deneyimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="c9620-200">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="c9620-201">Örnek olarak, MVU modelini kullanarak .NET MAUı 'de yazılmış aşağıdaki sayacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c9620-201">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="c9620-202">Daha fazla bilgi için bkz. [.net MAUI yol haritası](https://github.com/dotnet/maui/wiki/Roadmap)ve [.net MAUI makalesine giriş](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="c9620-202">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9620-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9620-203">See also</span></span>

- [<span data-ttu-id="c9620-204">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="c9620-204">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="c9620-205">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c9620-205">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
