---
title: .NET standart yenilikler nelerdir?
description: Bu makalede, yeni özellikler ve geliştirmeler her yeni sürümünde .NET standart bulunan özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591495"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="34a3e-103">.NET standart yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="34a3e-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="34a3e-104">.NET standart sürümü tutulan bir dizi standart bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir olması gereken API tanımlayan bir resmi belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="34a3e-105">.NET standart kitaplığı geliştiricileri yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="34a3e-106">.NET standart sürümünü hedefleyen bir kitaplık standart bu sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulaması üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="34a3e-107">En son .NET standart 2.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="34a3e-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="34a3e-108">.NET Core iş yükü yüklü .NET Core 2.0 SDK'sı yanı sıra Visual Studio 2017 sürüm 15.3 ile dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="34a3e-109">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="34a3e-109">Supported .NET implementations</span></span>

<span data-ttu-id="34a3e-110">.NET standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="34a3e-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="34a3e-111">.NET core 2.0 veya üstü</span><span class="sxs-lookup"><span data-stu-id="34a3e-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="34a3e-112">.NET framework 4.6.1 veya daha yenisi</span><span class="sxs-lookup"><span data-stu-id="34a3e-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="34a3e-113">Mono 5.4 veya üstü</span><span class="sxs-lookup"><span data-stu-id="34a3e-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="34a3e-114">Xamarin.iOS 10.14 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="34a3e-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="34a3e-115">Xamarin.Mac 3.8 ya da daha yeni</span><span class="sxs-lookup"><span data-stu-id="34a3e-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="34a3e-116">Xamarin.Android 8.0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="34a3e-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="34a3e-117">Evrensel Windows platformu 10.0.16299 veya daha yenisi</span><span class="sxs-lookup"><span data-stu-id="34a3e-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="34a3e-118">.NET standart 2.0 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="34a3e-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="34a3e-119">.NET standart 2.0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="34a3e-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="34a3e-120">Fazla genişletilmiş bir API kümesi</span><span class="sxs-lookup"><span data-stu-id="34a3e-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="34a3e-121">Sürüm 1.6 ile .NET standart API'leri daha küçük bir kısmı dahil.</span><span class="sxs-lookup"><span data-stu-id="34a3e-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="34a3e-122">Dışlanan bunlar arasında .NET Framework veya Xamarin yaygın olarak kullanılan birçok API'ları bulunuyordu.</span><span class="sxs-lookup"><span data-stu-id="34a3e-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="34a3e-123">Uygulamalar ve birden çok .NET uygulamalarında hedefleyen kitaplıklar geliştirirken geliştiriciler bilinen API'leri uygun donanımlarının Bul gerektirdiğinden, geliştirme, daha karmaşık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="34a3e-124">.NET standart 2.0, .NET standart 1.6 içinde standard'ın önceki sürümünü kullanılabilir olan çok fazla 20.000 daha fazla API'leri ekleyerek bu sınırlamaya giderir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="34a3e-125">.NET standart 2.0 için eklenene API'ları listesi için bkz: [.NET standart 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="34a3e-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="34a3e-126">Bazı eklemeler <xref:System> ad alanı .NET standart 2.0 içerir:</span><span class="sxs-lookup"><span data-stu-id="34a3e-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="34a3e-127">Desteği <xref:System.AppDomain> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="34a3e-128">Diziler ek üyelerinden ile çalışmak için daha iyi destek <xref:System.Array> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="34a3e-129">Ek üyeleri öznitelikleri ile çalışmak için daha iyi destek <xref:System.Attribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="34a3e-130">Daha iyi Takvim desteği ve ek biçimlendirme seçeneklerini <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="34a3e-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="34a3e-131">Ek <xref:System.Decimal> işlevselliği yuvarlama.</span><span class="sxs-lookup"><span data-stu-id="34a3e-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="34a3e-132">Ek işlevsellik <xref:System.Environment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="34a3e-133">Gelişmiş atık toplayıcı üzerinde denetim <xref:System.GC> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="34a3e-134">Dize karşılaştırması, numaralandırma ve içinde normalleştirme için gelişmiş destek <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="34a3e-135">Ayarlamaları ve geçiş saat gün ışığından yararlanma desteği <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="34a3e-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="34a3e-136">İşlevindeki'önemli ölçüde geliştirilmiş <xref:System.Type> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34a3e-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="34a3e-137">Bir özel durum Oluşturucusu ile ekleyerek nesneleri seri durumdan çıkarma özel durumu için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="34a3e-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="34a3e-138">.NET Framework kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="34a3e-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="34a3e-139">Kitaplıkları zorlamayı çoğunluğu .NET Framework yerine .NET standart hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="34a3e-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="34a3e-140">Ancak, bu kitaplıkları çağrılarında .NET standart 2.0 dahil API'lerine çoğu.</span><span class="sxs-lookup"><span data-stu-id="34a3e-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="34a3e-141">.NET standart 2.0 ile başlayarak, .NET Framework kitaplıkları .NET standart bir kitaplıktan kullanarak erişebilirsiniz bir [uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="34a3e-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="34a3e-142">Bu uyumluluk katmanı geliştiricileri için saydamdır; .NET Framework kitaplıkları yararlanmak için bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="34a3e-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="34a3e-143">.NET Framework sınıf kitaplığı tarafından çağırılan API'lerin .NET standart 2.0 dahil edilmesi gerektiğini tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="34a3e-144">Visual Basic desteği</span><span class="sxs-lookup"><span data-stu-id="34a3e-144">Support for Visual Basic</span></span>

<span data-ttu-id="34a3e-145">Visual Basic'te .NET standart kitaplıkları şimdi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34a3e-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="34a3e-146">Visual Studio 2017 sürüm 15.3 kullanarak Visual Basic geliştiricileri için ya da yüklü daha sonra .NET Core iş yükü ile Visual Studio artık bir .NET standart sınıf kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="34a3e-147">Diğer geliştirme araçları ve ortamlar kullanan Visual Basic geliştiricileri için kullandığınız [dotnet yeni](../../core/tools/dotnet-new.md) .NET standart kitaplığı projesi oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="34a3e-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="34a3e-148">Daha fazla bilgi için bkz: [.NET standart kitaplıkları için araç desteği](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="34a3e-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="34a3e-149">.NET standart kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="34a3e-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="34a3e-150">.NET Core 2.0 ve .NET standart 2.0, hem Visual Studio 2017'in çıkışıyla ve [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) araç .NET standart kitaplıkları oluşturmak için desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="34a3e-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="34a3e-151">Visual Studio ile yüklerseniz **.NET Core platformlar arası geliştirme** iş yükü, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET standart 2.0 kitaplığı projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34a3e-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="34a3e-152">C#</span><span class="sxs-lookup"><span data-stu-id="34a3e-152">C#</span></span>](#tab/csharp)

![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-cs.png)

<span data-ttu-id="34a3e-154">Aşağıdaki .NET Core CLI kullanıyorsanız [dotnet yeni](../../core/tools/dotnet-new.md) komut .NET standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="34a3e-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="34a3e-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34a3e-155">Visual Basic</span></span>](#tab/vb)

![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-vb.png)

<span data-ttu-id="34a3e-157">Aşağıdaki .NET Core CLI kullanıyorsanız [dotnet yeni](../../core/tools/dotnet-new.md) komut .NET standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="34a3e-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="34a3e-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34a3e-158">See also</span></span>

[<span data-ttu-id="34a3e-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="34a3e-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="34a3e-160">.NET standart giriş</span><span class="sxs-lookup"><span data-stu-id="34a3e-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
