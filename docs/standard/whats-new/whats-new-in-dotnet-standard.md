---
title: .NET Standard'daki yenilikler
description: Bu makalede, yeni özellikler ve geliştirmeler her .NET Standard'ın yeni sürümünde bulunan özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8810508bc61f6fd625b1485f199249a96b2686e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425439"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="d24ba-103">.NET Standard'daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="d24ba-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="d24ba-104">.NET standard'ın bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir API sürümü tutulan kümesini tanımlayan bir resmi belirtimi standarttır.</span><span class="sxs-lookup"><span data-stu-id="d24ba-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="d24ba-105">.NET Standard kitaplığı geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="d24ba-106">.NET Standard bir sürümü hedefleyen bir kitaplık standart sürümünün desteklediği tüm .NET Framework, .NET Core ve Xamarin uygulaması üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="d24ba-107">En son .NET Standard 2.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d24ba-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="d24ba-108">.NET Core iş yükü yüklenmiş olan .NET Core 2.0 SDK'sını yanı sıra Visual Studio 2017 sürüm 15.3 ile dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="d24ba-109">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d24ba-109">Supported .NET implementations</span></span>

<span data-ttu-id="d24ba-110">.NET Standard 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="d24ba-111">.NET core 2.0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="d24ba-112">.NET framework 4.6.1 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="d24ba-113">Mono 5.4 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="d24ba-114">Xamarin.iOS 10.14 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="d24ba-115">Xamarin.Mac 3.8 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="d24ba-116">Xamarin.Android 8.0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="d24ba-117">Evrensel Windows platformu 10.0.16299 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="d24ba-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="d24ba-118">.NET Standard 2.0 yenilikler</span><span class="sxs-lookup"><span data-stu-id="d24ba-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="d24ba-119">.NET Standard 2.0 aşağıdaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="d24ba-120">Büyük ölçüde genişletilmiş bir API kümesi</span><span class="sxs-lookup"><span data-stu-id="d24ba-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="d24ba-121">Sürüm 1.6 .NET Standard API'leri daha küçük bir kısmı dahil.</span><span class="sxs-lookup"><span data-stu-id="d24ba-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="d24ba-122">Arasında olanlar hariç, Xamarin ve .NET Framework içinde yaygın olarak kullanılan birçok API'leri yoktu.</span><span class="sxs-lookup"><span data-stu-id="d24ba-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="d24ba-123">Uygulamalar ve birden çok .NET uygulamaları hedefleyen kitaplıklar geliştirirken geliştiriciler için tanıdık API'lerini uygun değiştirmeler öğrenin gerektirdiğinden, geliştirme, daha karmaşık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="d24ba-124">.NET Standard 2.0, .NET standart 1.6, standart'ın önceki sürümünü kullanılabilen çok 20. 000'den daha fazla API ekleyerek bu sınırlama yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="d24ba-125">.NET Standard 2.0 eklenmiş olan API'leri bir listesi için bkz. [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="d24ba-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="d24ba-126">Bazı eklemeler <xref:System> ad alanında .NET Standard 2.0 içerir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="d24ba-127">Destek <xref:System.AppDomain> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="d24ba-128">Ek üyeleri dizilerden ile çalışmak için daha iyi destek <xref:System.Array> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="d24ba-129">Ek üye öznitelikleri ile çalışmak için daha iyi destek <xref:System.Attribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="d24ba-130">Daha iyi destek ve ek biçimlendirme seçenekleri için Takvim <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="d24ba-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="d24ba-131">Ek <xref:System.Decimal> işlevselliği yuvarlama.</span><span class="sxs-lookup"><span data-stu-id="d24ba-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="d24ba-132">Ek işlevsellik <xref:System.Environment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="d24ba-133">Gelişmiş çöp toplayıcı üzerinde denetim <xref:System.GC> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="d24ba-134">Dize karşılaştırması, numaralandırma ve normalleştirme içinde için gelişmiş destek <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="d24ba-135">Destek ayarlamalar ve geçiş süreleri içinde ışığından <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="d24ba-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="d24ba-136">İşlevindeki'önemli ölçüde geliştirilmiş <xref:System.Type> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24ba-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="d24ba-137">Bir özel durum oluşturucuyla ekleyerek nesneleri seri durumdan çıkarma özel durum için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d24ba-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="d24ba-138">.NET Framework kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="d24ba-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="d24ba-139">.NET Framework yerine .NET Standard kitaplıkları büyük çoğunluğu hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="d24ba-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="d24ba-140">Ancak, bu kitaplıkları çağrılarında .NET Standard 2.0 içinde bulunan API'lerin çoğu.</span><span class="sxs-lookup"><span data-stu-id="d24ba-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="d24ba-141">.NET Standard 2.0 ile başlayarak, .NET Framework kitaplıkları bir .NET Standard Kitaplığı'ndan kullanarak erişebileceğiniz bir [uyumluluk dolgu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="d24ba-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="d24ba-142">Bu uyumluluk katmanı, geliştiriciler için saydamdır; .NET Framework kitaplıkları yararlanmak için herhangi bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d24ba-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="d24ba-143">.NET Framework sınıf kitaplığının adlı API'leri .NET Standard 2.0 dahil edilmesi gerektiğini tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="d24ba-144">Visual Basic için destek</span><span class="sxs-lookup"><span data-stu-id="d24ba-144">Support for Visual Basic</span></span>

<span data-ttu-id="d24ba-145">Artık Visual Basic'te .NET standart kitaplıkları da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="d24ba-146">Visual Studio 2017 sürüm 15.3 kullanan Visual Basic geliştiriciler için ya da daha sonra .NET Core iş yükü yüklenmiş olan Visual Studio artık .NET standart sınıf kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="d24ba-147">Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiricileri için kullanabileceğiniz [yeni dotnet](../../core/tools/dotnet-new.md) komutunu bir .NET Standard kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d24ba-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="d24ba-148">Daha fazla bilgi için [.NET standart kitaplıkları için araç desteği](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="d24ba-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="d24ba-149">.NET Standard kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="d24ba-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="d24ba-150">.NET Core 2.0 ve .NET Standard 2.0, hem Visual Studio 2017 sürümünde ve [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) araç .NET standart kitaplıkları oluşturmak için desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="d24ba-151">Visual Studio'ya yüklerseniz **.NET Core çoklu platform geliştirme** iş yükü, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2.0 kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d24ba-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="d24ba-152">C#</span><span class="sxs-lookup"><span data-stu-id="d24ba-152">C#</span></span>](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi ekleme](./media/std-project-cs.png)

<span data-ttu-id="d24ba-154">.NET Core CLI, aşağıdaki kullanıyorsanız [yeni dotnet](../../core/tools/dotnet-new.md) komut .NET Standard 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d24ba-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="d24ba-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d24ba-155">Visual Basic</span></span>](#tab/vb)

![Yeni .NET Standard kitaplığı projesi ekleme](./media/std-project-vb.png)

<span data-ttu-id="d24ba-157">.NET Core CLI, aşağıdaki kullanıyorsanız [yeni dotnet](../../core/tools/dotnet-new.md) komut .NET Standard 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d24ba-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="d24ba-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-158">See also</span></span>

[<span data-ttu-id="d24ba-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d24ba-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="d24ba-160">.NET Standard ile tanışın</span><span class="sxs-lookup"><span data-stu-id="d24ba-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
