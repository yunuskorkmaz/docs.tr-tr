---
title: .NET 5’teki yenilikler
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 11/18/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 077fb06db40519af2bf8ac2f659488acdf525aec
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916222"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="b53d8-103">.NET 5’teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b53d8-103">What's new in .NET 5</span></span>

<span data-ttu-id="b53d8-104">.NET 5,0, .NET Core 'un sonraki önemli sürümüdür 3,1.</span><span class="sxs-lookup"><span data-stu-id="b53d8-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="b53d8-105">Aşağıdaki iki nedenden dolayı .NET Core 4,0 yerine bu yeni sürüm .NET 5,0 ' i adlandırdık:</span><span class="sxs-lookup"><span data-stu-id="b53d8-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="b53d8-106">.NET Framework 4. x ile karışıklık oluşmasını önlemek için 4. x sürüm numaralarını atladık.</span><span class="sxs-lookup"><span data-stu-id="b53d8-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="b53d8-107">Bu, .NET 'in ana uygulamasının ileriye dönük olarak olduğunu vurgulamak için adından "Core" olarak bırakıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b53d8-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="b53d8-108">.NET 5,0, .NET Core veya .NET Framework 'dan daha fazla sayıda uygulamayı ve daha fazla platformu destekler.</span><span class="sxs-lookup"><span data-stu-id="b53d8-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="b53d8-109">ASP.NET Core 5,0, .NET 5,0 tabanlıdır ancak "Core" adını ASP.NET MVC 5 ile karıştırmamak için korur.</span><span class="sxs-lookup"><span data-stu-id="b53d8-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="b53d8-110">Benzer şekilde, Entity Framework Core 5,0 Entity Framework 5 ve 6 ' a karışmasını önlemek için "Core" adını korur.</span><span class="sxs-lookup"><span data-stu-id="b53d8-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="b53d8-111">.NET 5,0, .NET Core 3,1 ile karşılaştırıldığında aşağıdaki geliştirmeleri ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b53d8-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="b53d8-112">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="b53d8-113">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="b53d8-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="b53d8-114">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="b53d8-115"> Yeni özelliklerdeSystem.Text.Js</span><span class="sxs-lookup"><span data-stu-id="b53d8-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="b53d8-116">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="b53d8-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="b53d8-117">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="b53d8-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="b53d8-118">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="b53d8-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="b53d8-119">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="b53d8-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="b53d8-120">Çalışma zamanı kitaplıkları %80, [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için açıklama eklenmiş</span><span class="sxs-lookup"><span data-stu-id="b53d8-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="b53d8-121">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="b53d8-121">Performance improvements:</span></span>
  - [<span data-ttu-id="b53d8-122">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="b53d8-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="b53d8-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b53d8-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="b53d8-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b53d8-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="b53d8-125">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="b53d8-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="b53d8-126">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="b53d8-127">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="b53d8-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="b53d8-128">.NET 5,0 .NET Framework değiştirmez</span><span class="sxs-lookup"><span data-stu-id="b53d8-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="b53d8-129">.NET 5,0, .NET ' ün ve .NET Framework 4. x ' in ana uygulamasının hala desteklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="b53d8-130">Aşağıdaki teknolojilerin .NET Framework .NET 5,0 ' e bağlantı noktası yoktur, ancak .NET 5,0 ' de alternatifler vardır:</span><span class="sxs-lookup"><span data-stu-id="b53d8-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="b53d8-131">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="b53d8-131">Technology</span></span>            | <span data-ttu-id="b53d8-132">Önerilen alternatif</span><span class="sxs-lookup"><span data-stu-id="b53d8-132">Recommended alternative</span></span>                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b53d8-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="b53d8-133">Web Forms</span></span>             | <span data-ttu-id="b53d8-134">ASP.NET Core [Blazor](/aspnet/core/blazor) veya [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="b53d8-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="b53d8-135">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="b53d8-135">Windows Workflow (WF)</span></span> | [<span data-ttu-id="b53d8-136">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="b53d8-136">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

### <a name="windows-communication-foundation"></a><span data-ttu-id="b53d8-137">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b53d8-137">Windows Communication Foundation</span></span>

<span data-ttu-id="b53d8-138">[Windows Communication Foundation (WCF)](../framework/wcf/index.md) özgün uygulanması yalnızca Windows 'da desteklenir; ancak .NET Foundation 'da kullanılabilir bir istemci bağlantı noktası var.</span><span class="sxs-lookup"><span data-stu-id="b53d8-138">The original implementation of the [Windows Communication Foundation (WCF)](../framework/wcf/index.md) was only supported on Windows, however; there is a client port available from the .NET Foundation.</span></span> <span data-ttu-id="b53d8-139">Bu, tamamen [açık kaynak](https://github.com/dotnet/wcf), platformlar arası ve Microsoft tarafından desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-139">It is entirely [open source](https://github.com/dotnet/wcf), cross platform, and supported by Microsoft.</span></span> <span data-ttu-id="b53d8-140">Temel NuGet paketleri aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="b53d8-140">The core NuGet packages are listed below:</span></span>

- [<span data-ttu-id="b53d8-141">System. ServiceModel. dupleks</span><span class="sxs-lookup"><span data-stu-id="b53d8-141">System.ServiceModel.Duplex</span></span>](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [<span data-ttu-id="b53d8-142">System. ServiceModel. FEDERATION</span><span class="sxs-lookup"><span data-stu-id="b53d8-142">System.ServiceModel.Federation</span></span>](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [<span data-ttu-id="b53d8-143">System. ServiceModel. http</span><span class="sxs-lookup"><span data-stu-id="b53d8-143">System.ServiceModel.Http</span></span>](https://www.nuget.org/packages/System.ServiceModel.Http)
- [<span data-ttu-id="b53d8-144">System. ServiceModel. NetTcp</span><span class="sxs-lookup"><span data-stu-id="b53d8-144">System.ServiceModel.NetTcp</span></span>](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [<span data-ttu-id="b53d8-145">System. ServiceModel. Ilkel öğeler</span><span class="sxs-lookup"><span data-stu-id="b53d8-145">System.ServiceModel.Primitives</span></span>](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [<span data-ttu-id="b53d8-146">System. ServiceModel. Security</span><span class="sxs-lookup"><span data-stu-id="b53d8-146">System.ServiceModel.Security</span></span>](https://www.nuget.org/packages/System.ServiceModel.Security)

<span data-ttu-id="b53d8-147">Topluluk, belirtilen istemci kitaplıklarını karmaşıren sunucu bileşenlerini korur.</span><span class="sxs-lookup"><span data-stu-id="b53d8-147">The community maintains the server components that compliment the aforementioned client libraries.</span></span> <span data-ttu-id="b53d8-148">GitHub deposu [Corewcf](https://github.com/CoreWCF/CoreWCF)'de bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-148">The GitHub repository can be found at [CoreWCF](https://github.com/CoreWCF/CoreWCF).</span></span> <span data-ttu-id="b53d8-149">Sunucu bileşenleri Microsoft tarafından _resmi olarak desteklenmez._</span><span class="sxs-lookup"><span data-stu-id="b53d8-149">The server components are _not_ officially supported by Microsoft.</span></span> <span data-ttu-id="b53d8-150">WCF 'ye alternatif olarak, [GRPC](/aspnet/core/grpc)'yi düşünün.</span><span class="sxs-lookup"><span data-stu-id="b53d8-150">For an alternative to WCF, consider [gRPC](/aspnet/core/grpc).</span></span>

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="b53d8-151">.NET 5,0 .NET Standard değiştirmez</span><span class="sxs-lookup"><span data-stu-id="b53d8-151">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="b53d8-152">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-152">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="b53d8-153">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="b53d8-153">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="b53d8-154">.NET 5,0 uygulamaları ve kitaplıkları için, `net5.0` hedef Framework bilinen adı (TFM), `netcoreapp` ve tfms 'yi birleştirir ve değiştirir `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="b53d8-154">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="b53d8-155">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b53d8-155">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="b53d8-156">Daha fazla bilgi için bkz. [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="b53d8-156">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="b53d8-157">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-157">C# updates</span></span>

<span data-ttu-id="b53d8-158">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="b53d8-158">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="b53d8-159">.NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="b53d8-159">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="b53d8-160">Aşağıda bazı önemli noktalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b53d8-160">Here are a few highlights:</span></span>

- <span data-ttu-id="b53d8-161">Kayıtlar: değer tabanlı eşitlik semantiklerine sahip başvuru türleri ve yeni bir ifade tarafından desteklenen yıkıcı olmayan mutasyon `with` .</span><span class="sxs-lookup"><span data-stu-id="b53d8-161">Records: reference types with value-based equality semantics and non-destructive mutation supported by a new `with` expression.</span></span>
- <span data-ttu-id="b53d8-162">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="b53d8-162">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="b53d8-163">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="b53d8-163">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="b53d8-164">İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="b53d8-164">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="b53d8-165">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="b53d8-165">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="b53d8-166">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="b53d8-166">Source generators</span></span>

<span data-ttu-id="b53d8-167">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="b53d8-167">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="b53d8-168">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b53d8-168">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="b53d8-169">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="b53d8-169">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="b53d8-170">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="b53d8-170">F# updates</span></span>

<span data-ttu-id="b53d8-171">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b53d8-171">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="b53d8-172">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b53d8-172">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="b53d8-173">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="b53d8-173">Interpolated strings</span></span>

<span data-ttu-id="b53d8-174">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript, F # temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b53d8-174">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="b53d8-175">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="b53d8-175">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="b53d8-176">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-176">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="b53d8-177">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="b53d8-177">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="b53d8-178">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-178">Visual Basic updates</span></span>

<span data-ttu-id="b53d8-179">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="b53d8-179">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="b53d8-180">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="b53d8-180">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="b53d8-181">Description</span><span class="sxs-lookup"><span data-stu-id="b53d8-181">Description</span></span>                            | <span data-ttu-id="b53d8-182">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="b53d8-182">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="b53d8-183">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b53d8-183">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="b53d8-184">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b53d8-184">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="b53d8-185">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="b53d8-185">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="b53d8-186">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b53d8-186">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="b53d8-187">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b53d8-187">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="b53d8-188">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b53d8-188">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="b53d8-189">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="b53d8-189">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="b53d8-190">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b53d8-190">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="b53d8-191">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b53d8-191">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="b53d8-192">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="b53d8-192">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="b53d8-193">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="b53d8-193">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="b53d8-194">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b53d8-194">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="b53d8-195">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="b53d8-195">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="b53d8-196">Yeni özelliklerde System.Text.Js</span><span class="sxs-lookup"><span data-stu-id="b53d8-196">System.Text.Json new features</span></span>

<span data-ttu-id="b53d8-197">Ve [ üzerindeSystem.Text.Js](../standard/serialization/system-text-json-overview.md)için yeni özellikler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="b53d8-197">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="b53d8-198">Başvuruları koru ve döngüsel başvuruları işle</span><span class="sxs-lookup"><span data-stu-id="b53d8-198">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="b53d8-199">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-199">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="b53d8-200">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="b53d8-200">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="b53d8-201">Sabit türleri ve C# 9 kayıtlarını destekleme</span><span class="sxs-lookup"><span data-stu-id="b53d8-201">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="b53d8-202">Ortak olmayan özellik erişimcileri desteği</span><span class="sxs-lookup"><span data-stu-id="b53d8-202">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="b53d8-203">Destek alanları</span><span class="sxs-lookup"><span data-stu-id="b53d8-203">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="b53d8-204">Özelliği koşullu olarak Yoksay</span><span class="sxs-lookup"><span data-stu-id="b53d8-204">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="b53d8-205">Dize olmayan anahtar sözlüklerini destekleme</span><span class="sxs-lookup"><span data-stu-id="b53d8-205">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="b53d8-206">Özel dönüştürücülerin null işlemesine izin ver</span><span class="sxs-lookup"><span data-stu-id="b53d8-206">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="b53d8-207">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="b53d8-207">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="b53d8-208">Web varsayılanları ile JsonSerializerOptions oluşturma</span><span class="sxs-lookup"><span data-stu-id="b53d8-208">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a><span data-ttu-id="b53d8-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b53d8-209">See also</span></span>

- [<span data-ttu-id="b53d8-210">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="b53d8-210">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="b53d8-211">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b53d8-211">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="b53d8-212">.NET SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="b53d8-212">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
