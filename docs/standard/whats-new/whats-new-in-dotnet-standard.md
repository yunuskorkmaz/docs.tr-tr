---
title: .NET Standard’daki yenilikler
description: Bu makalede, .NET Standard her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: dotnet-whatsnew
ms.openlocfilehash: 299477a7375381fa7f8064562e2a68e221944a05
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817180"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="0021f-103">.NET Standard’daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="0021f-103">What's new in .NET Standard</span></span>

<span data-ttu-id="0021f-104">.NET Standard, standart sürümü olan .NET uygulamalarında kullanılabilir olması gereken, sürümlenmiş bir API kümesini tanımlayan bir biçimsel belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="0021f-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="0021f-105">.NET Standard, kitaplık geliştiricileri 'ne yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="0021f-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="0021f-106">.NET Standard sürümünü hedefleyen bir kitaplık, standart sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0021f-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="0021f-107">.NET Standard, .NET Core iş yükünü seçerken .NET Core SDK ve Visual Studio ile birlikte sunulur.</span><span class="sxs-lookup"><span data-stu-id="0021f-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="0021f-108">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0021f-108">Supported .NET implementations</span></span>

<span data-ttu-id="0021f-109">.NET Standard 2,0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0021f-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="0021f-110">.NET Core 2,0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="0021f-111">.NET Framework 4.6.1 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="0021f-112">Mono 5,4 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="0021f-113">Xamarin. iOS 10,14 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="0021f-114">Xamarin. Mac 3,8 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="0021f-115">Xamarin. Android 8,0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="0021f-116">Evrensel Windows Platformu 10.0.16299 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="0021f-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="0021f-117">.NET Standard 2,0 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="0021f-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="0021f-118">.NET Standard 2,0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0021f-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="0021f-119">Büyük ölçüde genişletilmiş bir API kümesi</span><span class="sxs-lookup"><span data-stu-id="0021f-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="0021f-120">Sürüm 1,6 ' den .NET Standard, API 'lerin bir karşılaştırarak küçük alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0021f-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="0021f-121">Dışlanlar arasında yaygın olarak .NET Framework veya Xamarin içinde kullanılan birçok API.</span><span class="sxs-lookup"><span data-stu-id="0021f-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="0021f-122">Bu, geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirdiklerinde tanıdık API 'Ler için uygun değişiklikleri bulmasını gerektirdiğinden geliştirmeyi karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="0021f-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="0021f-123">.NET Standard 2,0, standart bir önceki sürümü olan .NET Standard 1,6 ' de bulunandan daha fazla 20.000 ' den fazla API ekleyerek bu sınırlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="0021f-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="0021f-124">2,0 .NET Standard eklenen API 'lerin bir listesi için, bkz. [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="0021f-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="0021f-125"><xref:System>.NET Standard 2,0 ' deki ad alanına yapılan eklemelerin bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0021f-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="0021f-126">Sınıfı için destek <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="0021f-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="0021f-127">Sınıfında ek üyelerden diziler ile çalışmaya yönelik daha iyi destek <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="0021f-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="0021f-128">Sınıfında ek üyelerin öznitelikleriyle çalışma için daha iyi destek <xref:System.Attribute> .</span><span class="sxs-lookup"><span data-stu-id="0021f-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="0021f-129">Daha iyi takvim desteği ve değerler için ek biçimlendirme seçenekleri <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="0021f-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="0021f-130">Ek <xref:System.Decimal> yuvarlama işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="0021f-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="0021f-131">Sınıfında ek işlevsellik <xref:System.Environment> .</span><span class="sxs-lookup"><span data-stu-id="0021f-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="0021f-132">Sınıfından çöp toplayıcı üzerinde Gelişmiş denetim <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="0021f-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="0021f-133">Sınıfında dize karşılaştırma, numaralandırma ve normalleştirme için geliştirilmiş destek <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="0021f-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="0021f-134">Ve sınıflarında gün ışığından yararlanma ayarlamaları ve geçiş süreleri için <xref:System.TimeZoneInfo.AdjustmentRule> Destek <xref:System.TimeZoneInfo.TransitionTime> .</span><span class="sxs-lookup"><span data-stu-id="0021f-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="0021f-135">Sınıfında önemli ölçüde gelişmiş işlevsellik <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="0021f-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="0021f-136">Ve parametrelerine sahip bir özel durum Oluşturucusu ekleyerek özel durum nesnelerinin serisini kaldırma için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> .</span><span class="sxs-lookup"><span data-stu-id="0021f-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="0021f-137">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="0021f-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="0021f-138">Birçok kitaplık .NET Standard yerine .NET Framework hedef.</span><span class="sxs-lookup"><span data-stu-id="0021f-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="0021f-139">Ancak, bu kitaplıklardaki çağrıların çoğu .NET Standard 2,0 ' ye dahil olan API 'lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0021f-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="0021f-140">.NET Standard 2,0 ' den başlayarak, bir [Uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak bir .NET Standard kitaplığından .NET Framework kitaplıklarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0021f-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="0021f-141">Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için herhangi bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0021f-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="0021f-142">Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API 'Lerin .NET Standard 2,0 ' ye dahil edilmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0021f-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="0021f-143">Visual Basic için destek</span><span class="sxs-lookup"><span data-stu-id="0021f-143">Support for Visual Basic</span></span>

<span data-ttu-id="0021f-144">Artık Visual Basic .NET Standard kitaplıklarını geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0021f-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="0021f-145">.NET Core iş yükünün yüklü olduğu Visual Studio 2019 ve Visual Studio 2017 sürüm 15,3 veya üzeri bir .NET Standard sınıf kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="0021f-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="0021f-146">Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiriciler için, bir .NET Standard kitaplığı projesi oluşturmak üzere [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0021f-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="0021f-147">Daha fazla bilgi için bkz. [.NET Standard kitaplıkları Için araç desteği](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="0021f-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="0021f-148">.NET Standard kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="0021f-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="0021f-149">.NET Core 2,0 ve .NET Standard 2,0 sürümü ile hem Visual Studio 2017 hem de [.NET Core CLI](../../core/tools/index.md) .NET Standard kitaplıkları oluşturmak için araç desteğini içerir.</span><span class="sxs-lookup"><span data-stu-id="0021f-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="0021f-150">Visual Studio 'Yu **.NET Core platformlar arası geliştirme** iş yüküyle birlikte yüklerseniz, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2,0 kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0021f-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="0021f-151">C#</span><span class="sxs-lookup"><span data-stu-id="0021f-151">C#</span></span>](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-cs.png)

<span data-ttu-id="0021f-153">.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0021f-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="0021f-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0021f-154">Visual Basic</span></span>](#tab/vb)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-vb.png)

<span data-ttu-id="0021f-156">.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0021f-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="0021f-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0021f-157">See also</span></span>

- [<span data-ttu-id="0021f-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="0021f-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="0021f-159">.NET Standard tanıtımı</span><span class="sxs-lookup"><span data-stu-id="0021f-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [<span data-ttu-id="0021f-160">.NET SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="0021f-160">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
