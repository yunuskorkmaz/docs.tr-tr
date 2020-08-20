---
title: -langversion (C# derleyici seçenekleri)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656221"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="2f3a8-102">-langversion (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2f3a8-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="2f3a8-103">Derleyicinin yalnızca seçili C# dil belirtiminde bulunan sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f3a8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="2f3a8-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2f3a8-105">Arguments</span></span>

`option`

<span data-ttu-id="2f3a8-106">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="2f3a8-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="2f3a8-107">Varsayılan dil sürümü, uygulamanız için hedef çerçeveye ve SDK 'nın veya Visual Studio 'nun yüklü olduğu sürüme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="2f3a8-108">Bu kurallar, [dil sürümü yapılandırma](../configure-language-version.md#defaults) makalesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f3a8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f3a8-109">Remarks</span></span>

<span data-ttu-id="2f3a8-110">C# uygulamanız tarafından başvurulan meta veriler, **-langversion** derleyici seçeneği değildir.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="2f3a8-111">C# derleyicisinin her sürümü dil belirtimine uzantılar içerdiğinden, **-langversion** size derleyicinin önceki bir sürümünün eşdeğer işlevlerini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="2f3a8-112">Buna ek olarak, C# sürüm güncelleştirmeleri genellikle büyük .NET Framework sürümleriyle aynı olsa da yeni söz dizimi ve Özellikler ilgili çerçeve sürümüne bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="2f3a8-113">Yeni özellikler, C# düzeltmesine göre de yayınlanan yeni bir derleyici güncelleştirmesi gerektirirken, her bir özellik kendi minimum .NET API 'sine veya NuGet paketlerini veya diğer kitaplıkları ekleyerek alt düzey çerçeveler üzerinde çalışmasına izin veren ortak dil çalışma zamanı gereksinimlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="2f3a8-114">Kullandığınız dil **sürümü** ayarı ne olursa olsun,. exe veya. dll dosyanızı oluşturmak için ortak dil çalışma zamanının güncel sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="2f3a8-115">Tek bir istisna, **-langversion: ISO-1**altında çalışan arkadaş derlemelerdir ve [-moduleassemblyname (C# derleyici seçeneği)](./moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2f3a8-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="2f3a8-116">C# dil sürümünü belirtmenin diğer yolları için bkz. [C# dil sürümünü seçme](../configure-language-version.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="2f3a8-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> ..</span><span class="sxs-lookup"><span data-stu-id="2f3a8-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f3a8-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-118">C# language specification</span></span>

| <span data-ttu-id="2f3a8-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2f3a8-119">Version</span></span>          | <span data-ttu-id="2f3a8-120">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="2f3a8-120">Link</span></span>                       | <span data-ttu-id="2f3a8-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f3a8-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="2f3a8-122">C# 7,0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="2f3a8-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="2f3a8-123">Şu anda kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="2f3a8-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="2f3a8-124">C# 6,0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-124">C# 6.0</span></span>           | <span data-ttu-id="2f3a8-125">[Bağlantı][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="2f3a8-126">C# dil belirtimi sürüm 6-resmi olmayan taslak: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="2f3a8-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="2f3a8-127">C# 5,0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-127">C# 5.0</span></span>           | <span data-ttu-id="2f3a8-128">[PDF’yi İndir][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="2f3a8-129">Standart ECMA-334 5 sürümü</span><span class="sxs-lookup"><span data-stu-id="2f3a8-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="2f3a8-130">C# 3,0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-130">C# 3.0</span></span>           | <span data-ttu-id="2f3a8-131">[BELGEYI indir][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="2f3a8-132">C# dil belirtimi sürüm 3,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2f3a8-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="2f3a8-133">C# 2,0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-133">C# 2.0</span></span>           | <span data-ttu-id="2f3a8-134">[PDF’yi İndir][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="2f3a8-135">Standart ECMA-334 4 sürümü</span><span class="sxs-lookup"><span data-stu-id="2f3a8-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="2f3a8-136">C# 1,2</span><span class="sxs-lookup"><span data-stu-id="2f3a8-136">C# 1.2</span></span>           | <span data-ttu-id="2f3a8-137">[BELGEYI indir][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="2f3a8-138">C# dil belirtimi sürüm 1,2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2f3a8-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="2f3a8-139">C# 1,0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-139">C# 1.0</span></span>           | <span data-ttu-id="2f3a8-140">[BELGEYI indir][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="2f3a8-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="2f3a8-141">C# dil belirtimi sürüm 1,0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2f3a8-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="2f3a8-142">Tüm dil özelliklerini desteklemek için gereken en düşük SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="2f3a8-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="2f3a8-143">Aşağıdaki tabloda, SDK 'nın en düşük sürümü, ilgili dil sürümünü destekleyen C# derleyicisi ile listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="2f3a8-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="2f3a8-144">C# sürümü</span><span class="sxs-lookup"><span data-stu-id="2f3a8-144">C# version</span></span> | <span data-ttu-id="2f3a8-145">En düşük SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="2f3a8-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="2f3a8-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-146">C# 8.0</span></span>     | <span data-ttu-id="2f3a8-147">Microsoft Visual Studio/derleme araçları 2019, sürüm 16,3 veya .NET Core 3,0 SDK</span><span class="sxs-lookup"><span data-stu-id="2f3a8-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="2f3a8-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2f3a8-148">C# 7.3</span></span>     | <span data-ttu-id="2f3a8-149">Microsoft Visual Studio/derleme araçları 2017, sürüm 15,7</span><span class="sxs-lookup"><span data-stu-id="2f3a8-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="2f3a8-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="2f3a8-150">C# 7.2</span></span>     | <span data-ttu-id="2f3a8-151">Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5</span><span class="sxs-lookup"><span data-stu-id="2f3a8-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="2f3a8-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="2f3a8-152">C# 7.1</span></span>     | <span data-ttu-id="2f3a8-153">Microsoft Visual Studio/derleme araçları 2017, sürüm 15,3</span><span class="sxs-lookup"><span data-stu-id="2f3a8-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="2f3a8-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="2f3a8-154">C# 7.0</span></span>     | <span data-ttu-id="2f3a8-155">Microsoft Visual Studio/derleme araçları 2017</span><span class="sxs-lookup"><span data-stu-id="2f3a8-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="2f3a8-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="2f3a8-156">C# 6</span></span>       | <span data-ttu-id="2f3a8-157">Microsoft Visual Studio/derleme araçları 2015</span><span class="sxs-lookup"><span data-stu-id="2f3a8-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="2f3a8-158">C# 5</span><span class="sxs-lookup"><span data-stu-id="2f3a8-158">C# 5</span></span>       | <span data-ttu-id="2f3a8-159">Microsoft Visual Studio/derleme araçları 2012 veya paketlenmiş .NET Framework 4,5 derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="2f3a8-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="2f3a8-160">C# 4</span></span>       | <span data-ttu-id="2f3a8-161">Microsoft Visual Studio/derleme araçları 2010 veya paketlenmiş .NET Framework 4,0 derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="2f3a8-162">C# 3</span><span class="sxs-lookup"><span data-stu-id="2f3a8-162">C# 3</span></span>       | <span data-ttu-id="2f3a8-163">Microsoft Visual Studio/derleme araçları 2008 veya paketlenmiş .NET Framework 3,5 derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="2f3a8-164">C# 2</span><span class="sxs-lookup"><span data-stu-id="2f3a8-164">C# 2</span></span>       | <span data-ttu-id="2f3a8-165">Microsoft Visual Studio/derleme araçları 2005 veya paketlenmiş .NET Framework 2,0 derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="2f3a8-166">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="2f3a8-166">C# 1.0/1.2</span></span> | <span data-ttu-id="2f3a8-167">Microsoft Visual Studio/derleme araçları .NET 2002 veya paketlenmiş .NET Framework 1,0 derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f3a8-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="2f3a8-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f3a8-168">See also</span></span>

- [<span data-ttu-id="2f3a8-169">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2f3a8-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="2f3a8-170">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="2f3a8-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
