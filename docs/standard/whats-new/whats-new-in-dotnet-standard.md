---
title: .NET standart yenilikler nelerdir?
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3a5833bdfcf1e3433ea82403908e9a06a88cde27
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="b99ac-102">.NET standart yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="b99ac-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="b99ac-103">.NET standart sürümlü bir dizi standart bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir olması gereken API tanımlayan bir resmi belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="b99ac-104">.NET standart kitaplığı geliştiricileri yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="b99ac-105">.NET standart sürümünü hedefleyen bir kitaplık standart bu sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulaması üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="b99ac-106">En son .NET standart 2.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="b99ac-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="b99ac-107">.NET Core iş yükü yüklü .NET Core 2.0 SDK'sı yanı sıra Visual Studio 2017 sürüm 15.3 ile dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="b99ac-108">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="b99ac-108">Supported .NET implementations</span></span>

<span data-ttu-id="b99ac-109">.NET standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="b99ac-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="b99ac-110">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="b99ac-110">.NET Core 2.0</span></span>
- <span data-ttu-id="b99ac-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="b99ac-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="b99ac-112">Mono 5.4</span><span class="sxs-lookup"><span data-stu-id="b99ac-112">Mono 5.4</span></span>
- <span data-ttu-id="b99ac-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="b99ac-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="b99ac-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="b99ac-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="b99ac-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="b99ac-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="b99ac-116">Evrensel Windows platformu 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="b99ac-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="b99ac-117">.NET standart 2.0 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="b99ac-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="b99ac-118">.NET standart 2.0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b99ac-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="b99ac-119">**Fazla genişletilmiş bir API kümesi**</span><span class="sxs-lookup"><span data-stu-id="b99ac-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="b99ac-120">Sürüm 1.6 ile .NET standart API'leri daha küçük bir kısmı dahil.</span><span class="sxs-lookup"><span data-stu-id="b99ac-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="b99ac-121">Dışlanan bunlar arasında .NET Framework veya Xamarin yaygın olarak kullanılan birçok API'ları bulunuyordu.</span><span class="sxs-lookup"><span data-stu-id="b99ac-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="b99ac-122">Uygulamalar ve birden çok .NET uygulamalarında hedefleyen kitaplıklar geliştirirken geliştiriciler bilinen API'leri uygun donanımlarının Bul gerektirdiğinden, geliştirme, daha karmaşık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="b99ac-123">.NET standart 2.0, .NET standart 1.6 içinde standard'ın önceki sürümünü kullanılabilir olan çok fazla 20.000 daha fazla API'leri ekleyerek bu sınırlamaya giderir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="b99ac-124">.NET standart 2.0 için eklenene API'ları listesi için bkz: [.NET standart 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="b99ac-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="b99ac-125">Bazı eklemeler <xref:System> ad alanı .NET standart 2.0 içerir:</span><span class="sxs-lookup"><span data-stu-id="b99ac-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="b99ac-126">Desteği <xref:System.AppDomain> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="b99ac-127">Diziler ek üyelerinden ile çalışmak için daha iyi destek <xref:System.Array> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="b99ac-128">Ek üyeleri öznitelikleri ile çalışmak için daha iyi destek <xref:System.Attribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="b99ac-129">Daha iyi Takvim desteği ve ek biçimlendirme seçeneklerini <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="b99ac-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="b99ac-130">Ek <xref:System.Decimal> işlevselliği yuvarlama.</span><span class="sxs-lookup"><span data-stu-id="b99ac-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="b99ac-131">Ek işlevsellik <xref:System.Environment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="b99ac-132">Gelişmiş atık toplayıcı üzerinde denetim <xref:System.GC> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="b99ac-133">Dize karşılaştırması, numaralandırma ve içinde normalleştirme için gelişmiş destek <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="b99ac-134">Ayarlamaları ve geçiş saat gün ışığından yararlanma desteği <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="b99ac-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="b99ac-135">İşlevindeki'önemli ölçüde geliştirilmiş <xref:System.Type> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b99ac-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="b99ac-136">Bir özel durum Oluşturucusu ile ekleyerek nesneleri seri durumdan çıkarma özel durumu için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="b99ac-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="b99ac-137">**.NET Framework kitaplıkları için desteği**</span><span class="sxs-lookup"><span data-stu-id="b99ac-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="b99ac-138">Kitaplıkları zorlamayı çoğunluğu .NET Framework yerine .NET standart hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="b99ac-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="b99ac-139">Ancak, bu kitaplıkları çağrılarında .NET standart 2.0 dahil API'lerine çoğu.</span><span class="sxs-lookup"><span data-stu-id="b99ac-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="b99ac-140">.NET standart 2.0 ile başlayarak, .NET Framework kitaplıkları .NET standart bir kitaplıktan kullanarak erişebilirsiniz bir [uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="b99ac-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="b99ac-141">Bu uyumluluk katmanı geliştiricileri için saydamdır; .NET Framework kitaplıkları yararlanmak için bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b99ac-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="b99ac-142">.NET Framework sınıf kitaplığı tarafından çağırılan API'lerin .NET standart 2.0 dahil edilmesi gerektiğini tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="b99ac-143">**Visual Basic desteği**</span><span class="sxs-lookup"><span data-stu-id="b99ac-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="b99ac-144">Visual Basic'te .NET standart kitaplıkları şimdi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b99ac-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="b99ac-145">Visual Studio 2017 sürüm 15.3 kullanarak Visual Basic geliştiricileri için ya da yüklü daha sonra .NET Core iş yükü ile Visual Studio artık bir .NET standart sınıf kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="b99ac-146">Diğer geliştirme araçları ve ortamlar kullanan Visual Basic geliştiricileri için kullandığınız [dotnet yeni](../../core/tools/dotnet-new.md) .NET standart kitaplığı projesi oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="b99ac-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="b99ac-147">Daha fazla bilgi için bkz: [.NET standart kitaplıkları için araç desteği](#tooling).</span><span class="sxs-lookup"><span data-stu-id="b99ac-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="b99ac-148"><a name="tooling" />**.NET standart kitaplıkları için araç desteği**</span><span class="sxs-lookup"><span data-stu-id="b99ac-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="b99ac-149">.NET Core 2.0 ve .NET standart 2.0, hem Visual Studio 2017'in çıkışıyla ve [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) araç .NET standart kitaplıkları oluşturmak için desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="b99ac-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="b99ac-150">Visual Studio ile yüklerseniz **.NET Core platformlar arası geliştirme** iş yükü, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET standart 2.0 kitaplığı projesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b99ac-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="b99ac-151">C#</span><span class="sxs-lookup"><span data-stu-id="b99ac-151">C#</span></span>](#tab/csharp)
![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="b99ac-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b99ac-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-vb.png)
---

<span data-ttu-id="b99ac-155">Aşağıdaki .NET Core CLI kullanıyorsanız [dotnet yeni](../../core/tools/dotnet-new.md) komut .NET standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b99ac-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="b99ac-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b99ac-156">See Also</span></span>
<span data-ttu-id="b99ac-157">[.NET standart](../net-standard.md)
[.NET standart giriş](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="b99ac-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
