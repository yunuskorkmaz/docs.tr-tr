---
title: .NET 5’teki yenilikler
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 11/30/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: d0b8533dd63dd7d24f49e11093770b52d7daea89
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437868"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="95a14-103">.NET 5’teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="95a14-103">What's new in .NET 5</span></span>

<span data-ttu-id="95a14-104">.NET 5,0, .NET Core 'un sonraki önemli sürümüdür 3,1.</span><span class="sxs-lookup"><span data-stu-id="95a14-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="95a14-105">Aşağıdaki iki nedenden dolayı .NET Core 4,0 yerine bu yeni sürüm .NET 5,0 ' i adlandırdık:</span><span class="sxs-lookup"><span data-stu-id="95a14-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="95a14-106">.NET Framework 4. x ile karışıklık oluşmasını önlemek için 4. x sürüm numaralarını atladık.</span><span class="sxs-lookup"><span data-stu-id="95a14-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="95a14-107">Bu, .NET 'in ana uygulamasının ileriye dönük olarak olduğunu vurgulamak için adından "Core" olarak bırakıyoruz.</span><span class="sxs-lookup"><span data-stu-id="95a14-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="95a14-108">.NET 5,0, .NET Core veya .NET Framework 'dan daha fazla sayıda uygulamayı ve daha fazla platformu destekler.</span><span class="sxs-lookup"><span data-stu-id="95a14-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="95a14-109">ASP.NET Core 5,0, .NET 5,0 tabanlıdır ancak "Core" adını ASP.NET MVC 5 ile karıştırmamak için korur.</span><span class="sxs-lookup"><span data-stu-id="95a14-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="95a14-110">Benzer şekilde, Entity Framework Core 5,0 Entity Framework 5 ve 6 ' a karışmasını önlemek için "Core" adını korur.</span><span class="sxs-lookup"><span data-stu-id="95a14-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="95a14-111">.NET 5,0, .NET Core 3,1 ile karşılaştırıldığında aşağıdaki geliştirmeleri ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="95a14-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="95a14-112">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="95a14-113">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="95a14-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="95a14-114">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="95a14-115"> Yeni özelliklerdeSystem.Text.Js</span><span class="sxs-lookup"><span data-stu-id="95a14-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="95a14-116">Tek dosya uygulamaları</span><span class="sxs-lookup"><span data-stu-id="95a14-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="95a14-117">Uygulama kırpması</span><span class="sxs-lookup"><span data-stu-id="95a14-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="95a14-118">Windows ARM64 ve ARM64 iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="95a14-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="95a14-119">Döküm hata ayıklaması için araç desteği</span><span class="sxs-lookup"><span data-stu-id="95a14-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="95a14-120">Çalışma zamanı kitaplıkları %80, [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için açıklama eklenmiş</span><span class="sxs-lookup"><span data-stu-id="95a14-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="95a14-121">Performans iyileştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="95a14-121">Performance improvements:</span></span>
  - [<span data-ttu-id="95a14-122">Çöp toplama (GC)</span><span class="sxs-lookup"><span data-stu-id="95a14-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="95a14-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="95a14-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="95a14-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="95a14-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="95a14-125">Zaman uyumsuz ValueTask havuzu</span><span class="sxs-lookup"><span data-stu-id="95a14-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="95a14-126">Kapsayıcı boyutu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="95a14-127">Birçok daha fazla alan</span><span class="sxs-lookup"><span data-stu-id="95a14-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="95a14-128">.NET 5,0 .NET Framework değiştirmez</span><span class="sxs-lookup"><span data-stu-id="95a14-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="95a14-129">.NET 5,0, .NET ' ün ve .NET Framework 4. x ' in ana uygulamasının hala desteklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="95a14-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="95a14-130">Aşağıdaki teknolojilerin .NET Framework .NET 5,0 ' e bağlantı noktası yoktur, ancak .NET 5,0 ' de alternatifler vardır:</span><span class="sxs-lookup"><span data-stu-id="95a14-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="95a14-131">Teknoloji</span><span class="sxs-lookup"><span data-stu-id="95a14-131">Technology</span></span>            | <span data-ttu-id="95a14-132">Önerilen alternatif</span><span class="sxs-lookup"><span data-stu-id="95a14-132">Recommended alternative</span></span>                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="95a14-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="95a14-133">Web Forms</span></span>             | <span data-ttu-id="95a14-134">ASP.NET Core [Blazor](/aspnet/core/blazor) veya [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="95a14-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="95a14-135">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="95a14-135">Windows Workflow (WF)</span></span> | [<span data-ttu-id="95a14-136">Açık kaynaklı CoreWF</span><span class="sxs-lookup"><span data-stu-id="95a14-136">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

### <a name="windows-communication-foundation"></a><span data-ttu-id="95a14-137">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="95a14-137">Windows Communication Foundation</span></span>

<span data-ttu-id="95a14-138">[Windows Communication Foundation (WCF)](../framework/wcf/index.md) özgün uygulanması yalnızca Windows 'da desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="95a14-138">The original implementation of [Windows Communication Foundation (WCF)](../framework/wcf/index.md) was only supported on Windows.</span></span> <span data-ttu-id="95a14-139">Ancak, .NET Foundation 'da kullanılabilir bir istemci bağlantı noktası vardır.</span><span class="sxs-lookup"><span data-stu-id="95a14-139">However, there is a client port available from the .NET Foundation.</span></span> <span data-ttu-id="95a14-140">Bu, tamamen [açık kaynak](https://github.com/dotnet/wcf), platformlar arası ve Microsoft tarafından desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="95a14-140">It is entirely [open source](https://github.com/dotnet/wcf), cross platform, and supported by Microsoft.</span></span> <span data-ttu-id="95a14-141">Temel NuGet paketleri aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="95a14-141">The core NuGet packages are listed below:</span></span>

- [<span data-ttu-id="95a14-142">System. ServiceModel. dupleks</span><span class="sxs-lookup"><span data-stu-id="95a14-142">System.ServiceModel.Duplex</span></span>](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [<span data-ttu-id="95a14-143">System. ServiceModel. FEDERATION</span><span class="sxs-lookup"><span data-stu-id="95a14-143">System.ServiceModel.Federation</span></span>](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [<span data-ttu-id="95a14-144">System. ServiceModel. http</span><span class="sxs-lookup"><span data-stu-id="95a14-144">System.ServiceModel.Http</span></span>](https://www.nuget.org/packages/System.ServiceModel.Http)
- [<span data-ttu-id="95a14-145">System. ServiceModel. NetTcp</span><span class="sxs-lookup"><span data-stu-id="95a14-145">System.ServiceModel.NetTcp</span></span>](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [<span data-ttu-id="95a14-146">System. ServiceModel. Ilkel öğeler</span><span class="sxs-lookup"><span data-stu-id="95a14-146">System.ServiceModel.Primitives</span></span>](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [<span data-ttu-id="95a14-147">System. ServiceModel. Security</span><span class="sxs-lookup"><span data-stu-id="95a14-147">System.ServiceModel.Security</span></span>](https://www.nuget.org/packages/System.ServiceModel.Security)

<span data-ttu-id="95a14-148">Topluluk, belirtilen istemci kitaplıklarını tamamlayan sunucu bileşenlerini korur.</span><span class="sxs-lookup"><span data-stu-id="95a14-148">The community maintains the server components that complement the aforementioned client libraries.</span></span> <span data-ttu-id="95a14-149">GitHub deposu [Corewcf](https://github.com/CoreWCF/CoreWCF)'de bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="95a14-149">The GitHub repository can be found at [CoreWCF](https://github.com/CoreWCF/CoreWCF).</span></span> <span data-ttu-id="95a14-150">Sunucu bileşenleri Microsoft tarafından _resmi olarak desteklenmez._</span><span class="sxs-lookup"><span data-stu-id="95a14-150">The server components are _not_ officially supported by Microsoft.</span></span> <span data-ttu-id="95a14-151">WCF 'ye alternatif olarak, [GRPC](/aspnet/core/grpc)'yi düşünün.</span><span class="sxs-lookup"><span data-stu-id="95a14-151">For an alternative to WCF, consider [gRPC](/aspnet/core/grpc).</span></span>

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="95a14-152">.NET 5,0 .NET Standard değiştirmez</span><span class="sxs-lookup"><span data-stu-id="95a14-152">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="95a14-153">Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="95a14-153">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="95a14-154">.NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="95a14-154">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="95a14-155">.NET 5,0 uygulamaları ve kitaplıkları için, `net5.0` hedef Framework bilinen adı (TFM), `netcoreapp` ve tfms 'yi birleştirir ve değiştirir `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="95a14-155">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="95a14-156">Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95a14-156">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="95a14-157">Daha fazla bilgi için bkz. [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="95a14-157">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="95a14-158">C# güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-158">C# updates</span></span>

<span data-ttu-id="95a14-159">.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur.</span><span class="sxs-lookup"><span data-stu-id="95a14-159">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="95a14-160">.NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="95a14-160">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="95a14-161">Aşağıda bazı önemli noktalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="95a14-161">Here are a few highlights:</span></span>

- <span data-ttu-id="95a14-162">Kayıtlar: değer tabanlı eşitlik semantiklerine sahip başvuru türleri ve yeni bir ifade tarafından desteklenen yıkıcı olmayan mutasyon `with` .</span><span class="sxs-lookup"><span data-stu-id="95a14-162">Records: reference types with value-based equality semantics and non-destructive mutation supported by a new `with` expression.</span></span>
- <span data-ttu-id="95a14-163">İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .</span><span class="sxs-lookup"><span data-stu-id="95a14-163">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="95a14-164">En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:</span><span class="sxs-lookup"><span data-stu-id="95a14-164">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="95a14-165">İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .</span><span class="sxs-lookup"><span data-stu-id="95a14-165">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="95a14-166">Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="95a14-166">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="95a14-167">Kaynak oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="95a14-167">Source generators</span></span>

<span data-ttu-id="95a14-168">Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor.</span><span class="sxs-lookup"><span data-stu-id="95a14-168">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="95a14-169">Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="95a14-169">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="95a14-170">Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="95a14-170">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="95a14-171">F # güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="95a14-171">F# updates</span></span>

<span data-ttu-id="95a14-172">F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="95a14-172">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="95a14-173">F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="95a14-173">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="95a14-174">Ara değerli dizeler</span><span class="sxs-lookup"><span data-stu-id="95a14-174">Interpolated strings</span></span>

<span data-ttu-id="95a14-175">C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript, F # temel dize ilişkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="95a14-175">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="95a14-176">Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır.</span><span class="sxs-lookup"><span data-stu-id="95a14-176">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="95a14-177">Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="95a14-177">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="95a14-178">Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir.</span><span class="sxs-lookup"><span data-stu-id="95a14-178">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="95a14-179">Visual Basic güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-179">Visual Basic updates</span></span>

<span data-ttu-id="95a14-180">.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="95a14-180">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="95a14-181">Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="95a14-181">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="95a14-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95a14-182">Description</span></span>                            | <span data-ttu-id="95a14-183">`dotnet new` parametresinin</span><span class="sxs-lookup"><span data-stu-id="95a14-183">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="95a14-184">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="95a14-184">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="95a14-185">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="95a14-185">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="95a14-186">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="95a14-186">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="95a14-187">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="95a14-187">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="95a14-188">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="95a14-188">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="95a14-189">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="95a14-189">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="95a14-190">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="95a14-190">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="95a14-191">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="95a14-191">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="95a14-192">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="95a14-192">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="95a14-193">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="95a14-193">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="95a14-194">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="95a14-194">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="95a14-195">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="95a14-195">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="95a14-196">.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..</span><span class="sxs-lookup"><span data-stu-id="95a14-196">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="95a14-197">Yeni özelliklerde System.Text.Js</span><span class="sxs-lookup"><span data-stu-id="95a14-197">System.Text.Json new features</span></span>

<span data-ttu-id="95a14-198">Ve [ üzerindeSystem.Text.Js](../standard/serialization/system-text-json-overview.md)için yeni özellikler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="95a14-198">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="95a14-199">Başvuruları koru ve döngüsel başvuruları işle</span><span class="sxs-lookup"><span data-stu-id="95a14-199">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-preserve-references.md)
- [<span data-ttu-id="95a14-200">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="95a14-200">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="95a14-201">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="95a14-201">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-invalid-json.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="95a14-202">Sabit türleri ve C# 9 kayıtlarını destekleme</span><span class="sxs-lookup"><span data-stu-id="95a14-202">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-immutability.md)
- [<span data-ttu-id="95a14-203">Ortak olmayan özellik erişimcileri desteği</span><span class="sxs-lookup"><span data-stu-id="95a14-203">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-immutability.md)
- [<span data-ttu-id="95a14-204">Destek alanları</span><span class="sxs-lookup"><span data-stu-id="95a14-204">Support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="95a14-205">Özelliği koşullu olarak Yoksay</span><span class="sxs-lookup"><span data-stu-id="95a14-205">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-ignore-properties.md)
- [<span data-ttu-id="95a14-206">Dize olmayan anahtar sözlüklerini destekleme</span><span class="sxs-lookup"><span data-stu-id="95a14-206">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="95a14-207">Özel dönüştürücülerin null işlemesine izin ver</span><span class="sxs-lookup"><span data-stu-id="95a14-207">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="95a14-208">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="95a14-208">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-configure-options.md#copy-jsonserializeroptions)
- [<span data-ttu-id="95a14-209">Web varsayılanları ile JsonSerializerOptions oluşturma</span><span class="sxs-lookup"><span data-stu-id="95a14-209">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a><span data-ttu-id="95a14-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a14-210">See also</span></span>

- [<span data-ttu-id="95a14-211">Bir .NET ile yolculuğa</span><span class="sxs-lookup"><span data-stu-id="95a14-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="95a14-212">.NET 5 ' teki performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="95a14-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="95a14-213">.NET SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="95a14-213">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
