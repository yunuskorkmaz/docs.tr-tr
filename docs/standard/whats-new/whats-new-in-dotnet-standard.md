---
title: .NET Standard’daki Yenilikler
description: Bu makalede, .NET Standard'ın her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmiştir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921067"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="7251d-103">.NET Standard’daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="7251d-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="7251d-104">.NET Standardı, standardın bu sürümüne uygun .NET uygulamalarında bulunması gereken sürümlü API kümesini tanımlayan resmi bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="7251d-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="7251d-105">.NET Standardı kitaplık geliştiricileri hedeflenebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7251d-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="7251d-106">.NET Standart sürümünü hedefleyen bir kitaplık, standardın bu sürümünü destekleyen herhangi bir .NET Framework, .NET Core veya Xamarin uygulamasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7251d-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="7251d-107">.NET Standard'ın en son sürümü 2.0'dır.</span><span class="sxs-lookup"><span data-stu-id="7251d-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="7251d-108">.NET Core 2.0 SDK'nın yanı sıra .NET Core iş yükü yüklü Visual Studio 2017 sürüm 15.3 ile birlikte dahildir.</span><span class="sxs-lookup"><span data-stu-id="7251d-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="7251d-109">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7251d-109">Supported .NET implementations</span></span>

<span data-ttu-id="7251d-110">.NET Standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7251d-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="7251d-111">.NET Core 2.0 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="7251d-112">.NET Framework 4.6.1 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="7251d-113">Mono 5.4 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="7251d-114">Xamarin.iOS 10.14 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="7251d-115">Xamarin.Mac 3.8 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="7251d-116">Xamarin.Android 8.0 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="7251d-117">Evrensel Windows Platformu 10.0.16299 veya sonrası</span><span class="sxs-lookup"><span data-stu-id="7251d-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="7251d-118">.NET Standart 2.0'daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="7251d-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="7251d-119">.NET Standart 2.0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7251d-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="7251d-120">Büyük ölçüde genişletilmiş BIR API seti</span><span class="sxs-lookup"><span data-stu-id="7251d-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="7251d-121">Sürüm 1.6 aracılığıyla ,NET Standardı nispeten küçük bir API alt kümesini içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="7251d-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="7251d-122">Bu hariç arasında yaygın .NET Framework veya Xamarin kullanılan birçok API'ler vardı.</span><span class="sxs-lookup"><span data-stu-id="7251d-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="7251d-123">Geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirirken tanıdık API'ler için uygun yedekler bulmalarını gerektirdiğinden, bu durum geliştirmeyi karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="7251d-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="7251d-124">.NET Standart 2.0, standardın önceki sürümü olan .NET Standart 1.6'da bulunandan 20.000'den fazla API ekleyerek bu sınırlamayı giderir.</span><span class="sxs-lookup"><span data-stu-id="7251d-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="7251d-125">.NET Standart 2.0'a eklenen API'lerin listesi [için](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="7251d-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="7251d-126">.NET Standart 2.0'daki <xref:System> ad alanına yapılan eklemelerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7251d-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="7251d-127">Sınıf için <xref:System.AppDomain> destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="7251d-128"><xref:System.Array> Sınıftaki ek üyelerden gelen dizilerle çalışmak için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="7251d-129"><xref:System.Attribute> Sınıftaki ek üyelerin öznitelikleriyle çalışmak için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="7251d-130">Daha iyi takvim desteği ve <xref:System.DateTime> değerler için ek biçimlendirme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="7251d-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="7251d-131">Ek <xref:System.Decimal> yuvarlama işlevi.</span><span class="sxs-lookup"><span data-stu-id="7251d-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="7251d-132">Sınıfta ek <xref:System.Environment> işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="7251d-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="7251d-133"><xref:System.GC> Sınıf boyunca çöp toplayıcısı üzerinde geliştirilmiş kontrol.</span><span class="sxs-lookup"><span data-stu-id="7251d-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="7251d-134"><xref:System.String> Sınıfta dize karşılaştırması, numaralandırma ve normalleştirme için geliştirilmiş destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="7251d-135">Gün ışığından yararlanma ayarlamaları ve <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> sınıflarda geçiş süreleri için destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="7251d-136"><xref:System.Type> Sınıfta önemli ölçüde geliştirilmiş işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="7251d-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="7251d-137">Özel durum oluşturucusu <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreler ekleyerek özel durum nesnelerinin deserialization için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="7251d-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="7251d-138">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="7251d-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="7251d-139">Kitaplıkların ezici çoğunluğu .NET Standardı yerine .NET Framework'ü hedeflemektedir.</span><span class="sxs-lookup"><span data-stu-id="7251d-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="7251d-140">Ancak, bu kitaplıklarda yapılan çağrıların çoğu .NET Standart 2.0'da yer alan API'lere yapılır.</span><span class="sxs-lookup"><span data-stu-id="7251d-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="7251d-141">.NET Standard 2.0 ile başlayarak ,net framework kitaplıklarına bir .NET Standart kitaplığından [uyumluluk şim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7251d-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="7251d-142">Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için hiçbir şey yapmanıza gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="7251d-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="7251d-143">Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API'lerin .NET Standart 2.0'a dahil edilmesidir.</span><span class="sxs-lookup"><span data-stu-id="7251d-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="7251d-144">Visual Basic desteği</span><span class="sxs-lookup"><span data-stu-id="7251d-144">Support for Visual Basic</span></span>

<span data-ttu-id="7251d-145">Artık Visual Basic'te .NET Standart kitaplıkları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7251d-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="7251d-146">Visual Studio 2017 sürümünü 15.3 veya daha sonra .NET Core iş yükü yüklü olan Visual Basic geliştiricileri için Visual Studio artık bir .NET Standart Sınıf Kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="7251d-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="7251d-147">Diğer geliştirme araçlarını ve ortamlarını kullanan Visual Basic geliştiricileri için bir .NET Standart Kitaplığı projesi oluşturmak için [dotnet yeni](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7251d-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="7251d-148">Daha fazla bilgi [için .NET Standart kitaplıkları için Araçlama desteğine](#tooling-support-for-net-standard-libraries)bakın.</span><span class="sxs-lookup"><span data-stu-id="7251d-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="7251d-149">.NET Standart kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="7251d-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="7251d-150">.NET Core 2.0 ve .NET Standard 2.0'ın piyasaya sürülmesiyle, visual studio 2017 ve [.NET Core CLI,.NET](../../core/tools/index.md) Standart kitaplıklarını oluşturmak için araç desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="7251d-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="7251d-151">Visual Studio'yu **.NET Core platformlar arası geliştirme** iş yüküyle yüklerseniz, aşağıdaki şekilde belirtildiği gibi, bir proje şablonu kullanarak bir .NET Standart 2.0 kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7251d-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="7251d-152">C #</span><span class="sxs-lookup"><span data-stu-id="7251d-152">C#</span></span>](#tab/csharp)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-cs.png)

<span data-ttu-id="7251d-154">.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7251d-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="7251d-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7251d-155">Visual Basic</span></span>](#tab/vb)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-vb.png)

<span data-ttu-id="7251d-157">.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7251d-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="7251d-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7251d-158">See also</span></span>

- [<span data-ttu-id="7251d-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7251d-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="7251d-160">.NET Standardı Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="7251d-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
