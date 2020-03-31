---
title: .NET Standardı'ndaki yenilikler
description: Bu makalede, .NET Standard'ın her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmiştir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438197"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="3b250-103">.NET Standardı'ndaki yenilikler</span><span class="sxs-lookup"><span data-stu-id="3b250-103">What's new in .NET Standard</span></span>

<span data-ttu-id="3b250-104">.NET Standart, standardın bu sürümüne uygun .NET uygulamalarında bulunması gereken sürümlü BIR API kümesini tanımlayan resmi bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="3b250-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3b250-105">.NET Standard kütüphane geliştiricileri hedeflenir.</span><span class="sxs-lookup"><span data-stu-id="3b250-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3b250-106">.NET Standart sürümünü hedefleyen bir kitaplık, standardın bu sürümünü destekleyen herhangi bir .NET Framework, .NET Core veya Xamarin uygulamasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b250-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="3b250-107">.NET Standardı,.NET Core SDK'nın yanı sıra .NET Core iş yükünü seçtiğinizde Visual Studio ile birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="3b250-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="3b250-108">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="3b250-108">Supported .NET implementations</span></span>

<span data-ttu-id="3b250-109">.NET Standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3b250-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="3b250-110">.NET Core 2.0 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="3b250-111">.NET Framework 4.6.1 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="3b250-112">Mono 5.4 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="3b250-113">Xamarin.iOS 10.14 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="3b250-114">Xamarin.Mac 3.8 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="3b250-115">Xamarin.Android 8.0 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="3b250-116">Evrensel Windows Platformu 10.0.16299 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="3b250-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="3b250-117">.NET Standart 2.0'daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="3b250-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="3b250-118">.NET Standart 2.0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3b250-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="3b250-119">Büyük ölçüde genişletilmiş BIR API seti</span><span class="sxs-lookup"><span data-stu-id="3b250-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="3b250-120">.NET Standard, sürüm 1.6 aracılığıyla, nispeten küçük bir API alt kümesini içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="3b250-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="3b250-121">Bu hariç arasında yaygın .NET Framework veya Xamarin kullanılan birçok API'ler vardı.</span><span class="sxs-lookup"><span data-stu-id="3b250-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="3b250-122">Geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirirken tanıdık API'ler için uygun yedekler bulmalarını gerektirdiğinden, bu durum geliştirmeyi karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="3b250-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="3b250-123">.NET Standart 2.0, standardın önceki sürümü olan .NET Standart 1.6'da bulunandan 20.000'den fazla API ekleyerek bu sınırlamayı giderir.</span><span class="sxs-lookup"><span data-stu-id="3b250-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="3b250-124">.NET Standart 2.0'a eklenen API'lerin listesi [için](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="3b250-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="3b250-125">.NET Standart 2.0'daki <xref:System> ad alanına yapılan eklemelerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b250-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="3b250-126">Sınıf için <xref:System.AppDomain> destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="3b250-127"><xref:System.Array> Sınıftaki ek üyelerden gelen dizilerle çalışmak için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="3b250-128"><xref:System.Attribute> Sınıftaki ek üyelerin öznitelikleriyle çalışmak için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="3b250-129">Daha iyi takvim desteği ve <xref:System.DateTime> değerler için ek biçimlendirme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="3b250-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="3b250-130">Ek <xref:System.Decimal> yuvarlama işlevi.</span><span class="sxs-lookup"><span data-stu-id="3b250-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="3b250-131">Sınıfta ek <xref:System.Environment> işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="3b250-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="3b250-132"><xref:System.GC> Sınıf boyunca çöp toplayıcısı üzerinde geliştirilmiş kontrol.</span><span class="sxs-lookup"><span data-stu-id="3b250-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="3b250-133"><xref:System.String> Sınıfta dize karşılaştırması, numaralandırma ve normalleştirme için geliştirilmiş destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="3b250-134">Gün ışığından yararlanma ayarlamaları ve <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> sınıflarda geçiş süreleri için destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="3b250-135"><xref:System.Type> Sınıfta önemli ölçüde geliştirilmiş işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="3b250-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="3b250-136">Özel durum oluşturucusu <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreler ekleyerek özel durum nesnelerinin deserialization için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="3b250-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="3b250-137">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="3b250-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="3b250-138">Kütüphanelerin ezici çoğunluğu .NET Standardı yerine .NET Framework'ü hedeflemektedir.</span><span class="sxs-lookup"><span data-stu-id="3b250-138">The overwhelming majority of libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="3b250-139">Ancak, bu kitaplıklarda yapılan çağrıların çoğu .NET Standart 2.0'da yer alan API'lere yapılır.</span><span class="sxs-lookup"><span data-stu-id="3b250-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="3b250-140">.NET Standard 2.0 ile başlayarak ,.NET Framework kitaplıklarına bir .NET Standart kitaplığından [uyumluluk şim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b250-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="3b250-141">Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için hiçbir şey yapmanıza gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b250-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="3b250-142">Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API'lerin .NET Standart 2.0'a dahil edilmesidir.</span><span class="sxs-lookup"><span data-stu-id="3b250-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="3b250-143">Visual Basic desteği</span><span class="sxs-lookup"><span data-stu-id="3b250-143">Support for Visual Basic</span></span>

<span data-ttu-id="3b250-144">Artık Visual Basic'te .NET Standart kitaplıkları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b250-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="3b250-145">Visual Studio 2019 ve Visual Studio 2017 sürüm 15.3 veya daha sonra yüklü .NET Core iş yükü ile bir .NET Standart Sınıf Kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="3b250-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="3b250-146">Diğer geliştirme araçlarını ve ortamlarını kullanan Visual Basic geliştiricileri için bir .NET Standart Kitaplığı projesi oluşturmak için [dotnet yeni](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b250-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="3b250-147">Daha fazla bilgi [için .NET Standart kitaplıkları için Araçlama desteğine](#tooling-support-for-net-standard-libraries)bakın.</span><span class="sxs-lookup"><span data-stu-id="3b250-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="3b250-148">.NET Standart kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="3b250-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="3b250-149">.NET Core 2.0 ve .NET Standard 2.0'ın piyasaya sürülmesiyle, visual studio 2017 ve [.NET Core CLI,.NET](../../core/tools/index.md) Standart kitaplıklarını oluşturmak için araç desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="3b250-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="3b250-150">Visual Studio'yu **.NET Core platformlar arası geliştirme** iş yüküyle yüklerseniz, aşağıdaki şekilde belirtildiği gibi, bir proje şablonu kullanarak bir .NET Standart 2.0 kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b250-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="3b250-151">C#</span><span class="sxs-lookup"><span data-stu-id="3b250-151">C#</span></span>](#tab/csharp)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-cs.png)

<span data-ttu-id="3b250-153">.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3b250-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="3b250-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b250-154">Visual Basic</span></span>](#tab/vb)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-vb.png)

<span data-ttu-id="3b250-156">.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3b250-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="3b250-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b250-157">See also</span></span>

- [<span data-ttu-id="3b250-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3b250-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="3b250-159">.NET Standardı Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="3b250-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
