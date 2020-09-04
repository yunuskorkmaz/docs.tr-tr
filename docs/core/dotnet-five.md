---
title: .NET Core 'un .NET 5 sürümüne evrimi
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: f9fd0d09dbb65c2367ac268ea4a7055a299a7586
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89471991"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="515df-103">.NET Core 'un .NET 5 sürümüne evrimi</span><span class="sxs-lookup"><span data-stu-id="515df-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="515df-104">Bu makalede, .NET Core 'un sonraki sürümü olan 3,1 ' de bulunan .NET 5 ' te nelerin dahil olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="515df-104">This article details what is included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="515df-105">Sürüm numarası, .NET Framework 4. x ile karışıklık oluşmasını önlemek için 5,0.</span><span class="sxs-lookup"><span data-stu-id="515df-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="515df-106">Ve "çekirdek", .NET ' in ana uygulama olduğu için adından bırakılır.</span><span class="sxs-lookup"><span data-stu-id="515df-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="515df-107">.NET 5, .NET Core veya .NET Framework daha fazla sayıda uygulamayı ve daha fazlasını destekler.</span><span class="sxs-lookup"><span data-stu-id="515df-107">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="515df-108">.NET Core 'un bir bütün olarak .NET ekosistemini etkileyici yollarla geliştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="515df-108">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="515df-109">GitHub 'da açık kaynaklı bir proje olarak, topluluk katkılarını kutluyor ve zaman içinde gelişerek daha fazla iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="515df-109">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="515df-110">.NET Core 'un birkaç birincil özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="515df-110">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="515df-111">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="515df-111">Cross-platform</span></span>
> - <span data-ttu-id="515df-112">Açık kaynak</span><span class="sxs-lookup"><span data-stu-id="515df-112">Open-source</span></span>
> - <span data-ttu-id="515df-113">Yan yana yükleme</span><span class="sxs-lookup"><span data-stu-id="515df-113">Side-by-side installation</span></span>
> - <span data-ttu-id="515df-114">Küçük proje dosyaları (SDK stili)</span><span class="sxs-lookup"><span data-stu-id="515df-114">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="515df-115">Esnek dağıtım</span><span class="sxs-lookup"><span data-stu-id="515df-115">Flexible deployment</span></span>

<span data-ttu-id="515df-116">.NET 5 bu özellikleri genişleterek artımlı iyileştirmeler yapar:</span><span class="sxs-lookup"><span data-stu-id="515df-116">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="515df-117">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="515df-117">Single file apps</span></span>
- <span data-ttu-id="515df-118">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="515df-118">Windows ARM64, and ARM64 intrinsics</span></span>
- <span data-ttu-id="515df-119">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="515df-119">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="515df-120">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="515df-120">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="515df-121">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="515df-121">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="515df-122">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="515df-122">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="515df-123">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="515df-123">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="515df-124">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="515df-124">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="515df-125">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-125">Container size optimizations</span></span>
- [<span data-ttu-id="515df-126">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="515df-126">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="515df-127">C# derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-127">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="515df-128">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="515df-128">Tooling support for dump debugging</span></span>
- <span data-ttu-id="515df-129">Platform [null yapılabilir başvuru türleri](csharp/nullable-references.md) için %80 açıklanmalıdır</span><span class="sxs-lookup"><span data-stu-id="515df-129">Platform is 80% annotated for [nullable reference types](csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="515df-130">.NET 5 ne değildir?</span><span class="sxs-lookup"><span data-stu-id="515df-130">What .NET 5 is not</span></span>

<span data-ttu-id="515df-131">.NET 5 .NET Framework için bir değiştirme değildir.</span><span class="sxs-lookup"><span data-stu-id="515df-131">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="515df-132">Aşağıdaki teknolojilerin .NET Framework .NET 5 ' e bağlantı noktası yoktur, ancak .NET 5 ' te desteklenen alternatifler bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="515df-132">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="515df-133">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="515df-133">Technology</span></span>                             | <span data-ttu-id="515df-134">Öneri</span><span class="sxs-lookup"><span data-stu-id="515df-134">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="515df-135">Web Forms</span><span class="sxs-lookup"><span data-stu-id="515df-135">Web Forms</span></span>                              | [<span data-ttu-id="515df-136">ASP.NET Core Blazor</span><span class="sxs-lookup"><span data-stu-id="515df-136">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="515df-137">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="515df-137">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="515df-138">gRPC</span><span class="sxs-lookup"><span data-stu-id="515df-138">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="515df-139">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="515df-139">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="515df-140">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="515df-140">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="515df-141">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="515df-141">.NET Standard</span></span>

<span data-ttu-id="515df-142">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="515df-142">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="515df-143">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="515df-143">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="515df-144">`net5.0`Tfd, ve adlarını birleştirir ve değiştirir `netcoreapp` `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="515df-144">The `net5.0` TFM combines and replaces `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="515df-145">Bu TFM genellikle, .NET Standard gibi, platformlar arası çalışan teknolojileri dahil eder.</span><span class="sxs-lookup"><span data-stu-id="515df-145">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="515df-146">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="515df-146">However, if you're planning on sharing code between .NET Framework, .NET Core, and .NET 5 workloads - you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="515df-147">Daha fazla bilgi için bkz. [hedef çerçeveleri belirtme](standard/frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="515df-147">For more information, see [How to specify target frameworks](standard/frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="language-updates"></a><span data-ttu-id="515df-148">Dil güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-148">Language updates</span></span>

<span data-ttu-id="515df-149">.NET 5 ile .NET programlama dilleri iyileştirilmesine devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="515df-149">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="515df-150">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-150">C# updates</span></span>

<span data-ttu-id="515df-151">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="515df-151">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="515df-152">.NET 5, C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="515df-152">.NET 5 is paired with C# 9.</span></span> <span data-ttu-id="515df-153">C# 9, dile birçok yeni özellik getirir, bazı önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="515df-153">C# 9 brings many new features to the language, here are a few highlights:</span></span>

- <span data-ttu-id="515df-154">Kayıtlar: değer türleri gibi davranan ve yeni anahtar sözcüğünü dile tanıtan değişmez başvuru türleri `with` .</span><span class="sxs-lookup"><span data-stu-id="515df-154">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="515df-155">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="515df-155">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="515df-156">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="515df-156">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="515df-157">İşlevsel işaretçiler: ara dili (IL) sunan dil yapıları aşağıdaki işlem kodları `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="515df-157">Functional pointers: Language constructs that expose intermediate language (IL) the following opcodes `ldftn` and `calli`.</span></span>

<span data-ttu-id="515df-158">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="515df-158">For more information on the available C# 9 features, see [What's new in C# 9](csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="515df-159">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="515df-159">Source generators</span></span>

<span data-ttu-id="515df-160">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="515df-160">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="515df-161">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="515df-161">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="515df-162">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="515df-162">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="515df-163">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="515df-163">F# updates</span></span>

<span data-ttu-id="515df-164">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="515df-164">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="515df-165">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="515df-165">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="515df-166">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="515df-166">Interpolated strings</span></span>

<span data-ttu-id="515df-167">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript-F #, temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="515df-167">Similar to interpolated string in C#, and even JavaScript - F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="515df-168">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="515df-168">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="515df-169">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="515df-169">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="515df-170">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="515df-170">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <span data-ttu-id="515df-171">Daha fazla bilgi için bkz. [F # 5 ' teki](fsharp/whats-new/fsharp-50.md) yenilikler</span><span class="sxs-lookup"><span data-stu-id="515df-171">For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md)</span></span>

### <a name="visual-basic-updates"></a><span data-ttu-id="515df-172">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-172">Visual Basic updates</span></span>

<span data-ttu-id="515df-173">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="515df-173">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="515df-174">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="515df-174">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="515df-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="515df-175">Description</span></span>                            | <span data-ttu-id="515df-176">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="515df-176">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="515df-177">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="515df-177">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="515df-178">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="515df-178">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="515df-179">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="515df-179">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="515df-180">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="515df-180">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="515df-181">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="515df-181">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="515df-182">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="515df-182">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="515df-183">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="515df-183">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="515df-184">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="515df-184">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="515df-185">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="515df-185">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="515df-186">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="515df-186">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="515df-187">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="515df-187">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="515df-188">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="515df-188">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="515df-189">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](core/tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="515df-189">For more information on project templates from the .NET CLI, see [`dotnet new`](core/tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="515df-190">.NET MAUı</span><span class="sxs-lookup"><span data-stu-id="515df-190">.NET MAUI</span></span>

<span data-ttu-id="515df-191">.NET MAUı, giderek daha popüler Xamarin. Forms araç seti 'nin bir evrimi ve [DotNet/MAUI](https://github.com/dotnet/maui)'de GitHub 'da açık kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="515df-191">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="515df-192">.Net MAUı sayesinde, .NET geliştiricileri için seçim, tüm modern iş yüklerini destekleyen tek bir yığın sağlayan basitleştirilmiştir: Android, iOS, macOS ve Windows.</span><span class="sxs-lookup"><span data-stu-id="515df-192">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="515df-193">.NET MAUı ile birden çok platformu ve cihazı hedefleyen tek bir proje geliştirici deneyimi edinirsiniz.</span><span class="sxs-lookup"><span data-stu-id="515df-193">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="515df-194">.NET MAUı erken önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="515df-194">.NET MAUI is in early preview.</span></span> <span data-ttu-id="515df-195">Örnek kaynak kodu, [Xamarin/NET6-Samples](https://github.com/xamarin/net6-samples)adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="515df-195">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="515df-196">Model-Görünüm-güncelleştirme modeli</span><span class="sxs-lookup"><span data-stu-id="515df-196">Model-View-Update pattern</span></span>

<span data-ttu-id="515df-197">Geliştiriciler modern geliştirme düzenlerini sevdiğinde.</span><span class="sxs-lookup"><span data-stu-id="515df-197">Developers love modern development patterns.</span></span> <span data-ttu-id="515df-198">UI geliştirmeye yönelik akıcı bir yaklaşım, "karaağaç mimarisi" tarafından ilham [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) veya MVU deseninin bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="515df-198">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="515df-199">MVU veri ve durum yönetiminin tek yönlü bir akışını ve yalnızca gerekli değişiklikleri uygulayarak Kullanıcı arabirimini hızla güncelleştiren bir kod ilk geliştirme deneyimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="515df-199">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="515df-200">Örnek olarak, MVU modelini kullanarak .NET MAUı 'de yazılmış aşağıdaki sayacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="515df-200">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="515df-201">Daha fazla bilgi için bkz. [.net MAUI yol haritası](https://github.com/dotnet/maui/wiki/Roadmap)ve [.net MAUI makalesine giriş](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="515df-201">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="515df-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="515df-202">See also</span></span>

- [<span data-ttu-id="515df-203">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="515df-203">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="515df-204">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="515df-204">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
