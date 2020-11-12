---
title: .NET 5’teki yenilikler
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 11/06/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: efce75159cd631ad64ba03d4b65aaeb64ccdc809
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557031"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="2129a-103">.NET 5’teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="2129a-103">What's new in .NET 5</span></span>

<span data-ttu-id="2129a-104">.NET 5,0, .NET Core 'un sonraki önemli sürümüdür 3,1.</span><span class="sxs-lookup"><span data-stu-id="2129a-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="2129a-105">Aşağıdaki iki nedenden dolayı .NET Core 4,0 yerine bu yeni sürüm .NET 5,0 ' i adlandırdık:</span><span class="sxs-lookup"><span data-stu-id="2129a-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="2129a-106">.NET Framework 4. x ile karışıklık oluşmasını önlemek için 4. x sürüm numaralarını atladık.</span><span class="sxs-lookup"><span data-stu-id="2129a-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="2129a-107">Bu, .NET 'in ana uygulamasının ileriye dönük olarak olduğunu vurgulamak için adından "Core" olarak bırakıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2129a-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="2129a-108">.NET 5,0, .NET Core veya .NET Framework 'dan daha fazla sayıda uygulamayı ve daha fazla platformu destekler.</span><span class="sxs-lookup"><span data-stu-id="2129a-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="2129a-109">ASP.NET Core 5,0, .NET 5,0 tabanlıdır ancak "Core" adını ASP.NET MVC 5 ile karıştırmamak için korur.</span><span class="sxs-lookup"><span data-stu-id="2129a-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="2129a-110">Benzer şekilde, Entity Framework Core 5,0 Entity Framework 5 ve 6 ' a karışmasını önlemek için "Core" adını korur.</span><span class="sxs-lookup"><span data-stu-id="2129a-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="2129a-111">.NET 5,0, .NET Core 3,1 ile karşılaştırıldığında aşağıdaki geliştirmeleri ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="2129a-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="2129a-112">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="2129a-113">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="2129a-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="2129a-114">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="2129a-115"> Yeni özelliklerdeSystem.Text.Js</span><span class="sxs-lookup"><span data-stu-id="2129a-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="2129a-116">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="2129a-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="2129a-117">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="2129a-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="2129a-118">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="2129a-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="2129a-119">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="2129a-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="2129a-120">Çalışma zamanı kitaplıkları %80, [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için açıklama eklenmiş</span><span class="sxs-lookup"><span data-stu-id="2129a-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="2129a-121">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="2129a-121">Performance improvements:</span></span>
  - [<span data-ttu-id="2129a-122">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="2129a-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="2129a-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="2129a-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="2129a-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="2129a-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="2129a-125">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="2129a-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="2129a-126">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="2129a-127">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="2129a-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="2129a-128">.NET 5,0 .NET Framework değiştirmez</span><span class="sxs-lookup"><span data-stu-id="2129a-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="2129a-129">.NET 5,0, .NET ' ün ve .NET Framework 4. x ' in ana uygulamasının hala desteklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="2129a-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="2129a-130">Aşağıdaki teknolojilerin .NET Framework .NET 5,0 ' e bağlantı noktası yoktur, ancak .NET 5,0 ' de alternatifler vardır:</span><span class="sxs-lookup"><span data-stu-id="2129a-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="2129a-131">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="2129a-131">Technology</span></span>                             | <span data-ttu-id="2129a-132">Önerilen alternatif</span><span class="sxs-lookup"><span data-stu-id="2129a-132">Recommended alternative</span></span>                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2129a-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="2129a-133">Web Forms</span></span>                              | <span data-ttu-id="2129a-134">ASP.NET Core [Blazor](/aspnet/core/blazor) veya [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="2129a-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="2129a-135">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="2129a-135">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="2129a-136">gRPC</span><span class="sxs-lookup"><span data-stu-id="2129a-136">gRPC</span></span>](/aspnet/core/grpc)                                                                       |
| <span data-ttu-id="2129a-137">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="2129a-137">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="2129a-138">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="2129a-138">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="2129a-139">.NET 5,0 .NET Standard değiştirmez</span><span class="sxs-lookup"><span data-stu-id="2129a-139">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="2129a-140">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="2129a-140">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="2129a-141">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="2129a-141">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="2129a-142">.NET 5,0 uygulamaları ve kitaplıkları için, `net5.0` hedef Framework bilinen adı (TFM), `netcoreapp` ve tfms 'yi birleştirir ve değiştirir `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="2129a-142">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="2129a-143">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2129a-143">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="2129a-144">Daha fazla bilgi için bkz. [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2129a-144">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="2129a-145">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-145">C# updates</span></span>

<span data-ttu-id="2129a-146">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="2129a-146">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="2129a-147">.NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="2129a-147">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="2129a-148">Aşağıda bazı önemli noktalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2129a-148">Here are a few highlights:</span></span>

- <span data-ttu-id="2129a-149">Kayıtlar: değer türleri gibi davranan ve yeni anahtar sözcüğünü dile tanıtan değişmez başvuru türleri `with` .</span><span class="sxs-lookup"><span data-stu-id="2129a-149">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="2129a-150">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="2129a-150">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="2129a-151">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="2129a-151">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="2129a-152">İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="2129a-152">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="2129a-153">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="2129a-153">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="2129a-154">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="2129a-154">Source generators</span></span>

<span data-ttu-id="2129a-155">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="2129a-155">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="2129a-156">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2129a-156">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="2129a-157">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="2129a-157">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="2129a-158">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="2129a-158">F# updates</span></span>

<span data-ttu-id="2129a-159">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="2129a-159">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="2129a-160">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2129a-160">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="2129a-161">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="2129a-161">Interpolated strings</span></span>

<span data-ttu-id="2129a-162">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript, F # temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="2129a-162">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="2129a-163">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="2129a-163">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="2129a-164">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2129a-164">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="2129a-165">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2129a-165">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="2129a-166">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-166">Visual Basic updates</span></span>

<span data-ttu-id="2129a-167">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="2129a-167">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="2129a-168">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="2129a-168">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="2129a-169">Description</span><span class="sxs-lookup"><span data-stu-id="2129a-169">Description</span></span>                            | <span data-ttu-id="2129a-170">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="2129a-170">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="2129a-171">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="2129a-171">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="2129a-172">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="2129a-172">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="2129a-173">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="2129a-173">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="2129a-174">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="2129a-174">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="2129a-175">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="2129a-175">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="2129a-176">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="2129a-176">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="2129a-177">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="2129a-177">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="2129a-178">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="2129a-178">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="2129a-179">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="2129a-179">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="2129a-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="2129a-180">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="2129a-181">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="2129a-181">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="2129a-182">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="2129a-182">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="2129a-183">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="2129a-183">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="2129a-184">Yeni özelliklerde System.Text.Js</span><span class="sxs-lookup"><span data-stu-id="2129a-184">System.Text.Json new features</span></span>

<span data-ttu-id="2129a-185">Ve [ üzerindeSystem.Text.Js](../standard/serialization/system-text-json-overview.md)için yeni özellikler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="2129a-185">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="2129a-186">Başvuruları koru ve döngüsel başvuruları işle</span><span class="sxs-lookup"><span data-stu-id="2129a-186">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="2129a-187">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2129a-187">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="2129a-188">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="2129a-188">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="2129a-189">Sabit türleri ve C# 9 kayıtlarını destekleme</span><span class="sxs-lookup"><span data-stu-id="2129a-189">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="2129a-190">Ortak olmayan özellik erişimcileri desteği</span><span class="sxs-lookup"><span data-stu-id="2129a-190">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="2129a-191">Destek alanları</span><span class="sxs-lookup"><span data-stu-id="2129a-191">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="2129a-192">Özelliği koşullu olarak Yoksay</span><span class="sxs-lookup"><span data-stu-id="2129a-192">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="2129a-193">Dize olmayan anahtar sözlüklerini destekleme</span><span class="sxs-lookup"><span data-stu-id="2129a-193">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="2129a-194">Ortak olmayan özellik erişimcileri desteği</span><span class="sxs-lookup"><span data-stu-id="2129a-194">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="2129a-195">Özel dönüştürücülerin null işlemesine izin ver</span><span class="sxs-lookup"><span data-stu-id="2129a-195">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="2129a-196">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="2129a-196">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="2129a-197">Web varsayılanları ile JsonSerializerOptions oluşturma</span><span class="sxs-lookup"><span data-stu-id="2129a-197">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="net-maui"></a><span data-ttu-id="2129a-198">.NET MAUı</span><span class="sxs-lookup"><span data-stu-id="2129a-198">.NET MAUI</span></span>

<span data-ttu-id="2129a-199">.NET MAUı, giderek daha popüler Xamarin. Forms araç seti 'nin bir evrimi ve [DotNet/MAUI](https://github.com/dotnet/maui)'de GitHub 'da açık kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="2129a-199">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="2129a-200">.Net MAUı sayesinde, .NET geliştiricileri için seçim, tüm modern iş yüklerini destekleyen tek bir yığın sağlayan basitleştirilmiştir: Android, iOS, macOS ve Windows.</span><span class="sxs-lookup"><span data-stu-id="2129a-200">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="2129a-201">.NET MAUı ile birden çok platformu ve cihazı hedefleyen tek bir proje geliştirici deneyimi edinirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2129a-201">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2129a-202">.NET MAUı erken önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="2129a-202">.NET MAUI is in early preview.</span></span> <span data-ttu-id="2129a-203">Örnek kaynak kodu, [Xamarin/NET6-Samples](https://github.com/xamarin/net6-samples)adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2129a-203">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="2129a-204">Model-Görünüm-güncelleştirme modeli</span><span class="sxs-lookup"><span data-stu-id="2129a-204">Model-View-Update pattern</span></span>

<span data-ttu-id="2129a-205">Geliştiriciler modern geliştirme düzenlerini sevdiğinde.</span><span class="sxs-lookup"><span data-stu-id="2129a-205">Developers love modern development patterns.</span></span> <span data-ttu-id="2129a-206">UI geliştirmeye yönelik akıcı bir yaklaşım, "karaağaç mimarisi" tarafından ilham [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) veya MVU deseninin bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2129a-206">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="2129a-207">MVU veri ve durum yönetiminin tek yönlü bir akışını ve yalnızca gerekli değişiklikleri uygulayarak Kullanıcı arabirimini hızla güncelleştiren bir kod ilk geliştirme deneyimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="2129a-207">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="2129a-208">Örnek olarak, MVU modelini kullanarak .NET MAUı 'de yazılmış aşağıdaki sayacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2129a-208">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="2129a-209">Daha fazla bilgi için bkz. [.net MAUI yol haritası](https://github.com/dotnet/maui/wiki/Roadmap)ve [.net MAUI makalesine giriş](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="2129a-209">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="2129a-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2129a-210">See also</span></span>

- [<span data-ttu-id="2129a-211">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="2129a-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="2129a-212">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2129a-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="2129a-213">.NET SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="2129a-213">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
