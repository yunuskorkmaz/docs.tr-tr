---
title: -langversion (C# Derleyici Seçenekleri)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 299ff121bab87482b7cdcaebc8b43cb8a1b559ec
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="9b161-102">-langversion (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9b161-102">-langversion (C# Compiler Options)</span></span>
<span data-ttu-id="9b161-103">Derleyicinin yalnızca seçilen C# dil belirtimi dahil sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9b161-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b161-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b161-104">Syntax</span></span>  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b161-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b161-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="9b161-106">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9b161-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="9b161-107">Seçenek</span><span class="sxs-lookup"><span data-stu-id="9b161-107">Option</span></span>|<span data-ttu-id="9b161-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b161-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="9b161-109">default</span><span class="sxs-lookup"><span data-stu-id="9b161-109">default</span></span>|<span data-ttu-id="9b161-110">Derleyici destekleyebileceği en son sürümle gelen tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9b161-110">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="9b161-111">ISO-1</span><span class="sxs-lookup"><span data-stu-id="9b161-111">ISO-1</span></span>|<span data-ttu-id="9b161-112">ISO/IEC 23270:2003 C# (1.0/1.2) dahil sözdizimi derleyici kabul <sup id="TISO1"> [ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-112">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="9b161-113">ISO-2</span><span class="sxs-lookup"><span data-stu-id="9b161-113">ISO-2</span></span>|<span data-ttu-id="9b161-114">ISO/IEC 23270:2006 C# (2.0) dahil sözdizimi derleyici kabul <sup id="TISO2"> [ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-114">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="9b161-115">3</span><span class="sxs-lookup"><span data-stu-id="9b161-115">3</span></span>|<span data-ttu-id="9b161-116">C# 3.0 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS3"> [CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-116">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="9b161-117">4</span><span class="sxs-lookup"><span data-stu-id="9b161-117">4</span></span>|<span data-ttu-id="9b161-118">Derleyici dahil C# 4.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS4"> [CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-118">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="9b161-119">5</span><span class="sxs-lookup"><span data-stu-id="9b161-119">5</span></span>|<span data-ttu-id="9b161-120">Derleyici dahil C# 5.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS5"> [CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-120">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="9b161-121">6</span><span class="sxs-lookup"><span data-stu-id="9b161-121">6</span></span>|<span data-ttu-id="9b161-122">Derleyici dahil C# 6. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS6"> [CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-122">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="9b161-123">7</span><span class="sxs-lookup"><span data-stu-id="9b161-123">7</span></span>|<span data-ttu-id="9b161-124">Derleyici dahil C# 7. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS7"> [CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-124">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="9b161-125">7.1</span><span class="sxs-lookup"><span data-stu-id="9b161-125">7.1</span></span>|<span data-ttu-id="9b161-126">C# 7.1 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS71"> [CS71](#FCS71)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-126">The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup></span></span>|
|<span data-ttu-id="9b161-127">7.2</span><span class="sxs-lookup"><span data-stu-id="9b161-127">7.2</span></span>|<span data-ttu-id="9b161-128">C# 7.2 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS72"> [CS72](#FCS72)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-128">The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS72">[CS72](#FCS72)</sup></span></span>|
|<span data-ttu-id="9b161-129">7.3</span><span class="sxs-lookup"><span data-stu-id="9b161-129">7.3</span></span>|<span data-ttu-id="9b161-130">C# 7.3 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS73"> [CS73](#FCS73)</sup></span><span class="sxs-lookup"><span data-stu-id="9b161-130">The compiler accepts only syntax that is included in C# 7.3 or lower <sup id="TCS73">[CS73](#FCS73)</sup></span></span>|
|<span data-ttu-id="9b161-131">en son</span><span class="sxs-lookup"><span data-stu-id="9b161-131">latest</span></span>|<span data-ttu-id="9b161-132">Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9b161-132">The compiler accepts all valid language syntax that it can support.</span></span>|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="9b161-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b161-133">Remarks</span></span>  
 <span data-ttu-id="9b161-134">C# uygulamanız tarafından başvurulan meta veri değil tabi **- langversion** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9b161-134">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>  
  
 <span data-ttu-id="9b161-135">C# Derleyici her sürümü uzantıları dil belirtimi içerdiğinden **- langversion** Derleyici önceki bir sürümünü eşdeğer işlevselliğini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9b161-135">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="9b161-136">C# sürüm güncelleştirmelerini ile ana .net Framework sürümleri genellikle çakıştığı olsa da, ayrıca, özellikleri ve yeni sözdizimini mutlaka bu belirli framework sürümüne bağlı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="9b161-136">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="9b161-137">Yeni özelliklerin yanı sıra C# düzeltme de serbest yeni bir derleyici güncelleştirme kesinlikle gerektirir, ancak her belirli özellik kendi minimum .net API veya alt düzey çerçeveleri tarafından üzerinde çalışmasına izin verebilir ortak dil çalışma zamanı gereksinimleri vardır. NuGet paketlerini veya diğer kitaplıkları dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="9b161-137">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="9b161-138">Hangi **- langversion** ayarını kullanın, .exe veya .dll dosyası oluşturmak için geçerli ortak dil çalışma zamanı sürümünü kullanacak.</span><span class="sxs-lookup"><span data-stu-id="9b161-138">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="9b161-139">Tek istisnası arkadaş derlemeleri ve [- moduleassemblyname (C# derleyici seçeneği)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), hangi altında çalışan **- langversion: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="9b161-139">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9b161-140">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9b161-140">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="9b161-141">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="9b161-141">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="9b161-142">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="9b161-142">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="9b161-143">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9b161-143">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="9b161-144">Değiştirme **dil sürümü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="9b161-144">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="9b161-145">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b161-145">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="9b161-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b161-146">See Also</span></span>  
 [<span data-ttu-id="9b161-147">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9b161-147">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="9b161-148">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="9b161-148">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="9b161-149">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9b161-149">C# Language Specification</span></span>

|<span data-ttu-id="9b161-150">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9b161-150">Version</span></span>|<span data-ttu-id="9b161-151">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="9b161-151">Link</span></span>|<span data-ttu-id="9b161-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b161-152">Description</span></span>|
|-------|----|-----------|
|<span data-ttu-id="9b161-153">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="9b161-153">C# 1.0</span></span>|[<span data-ttu-id="9b161-154">Belge indirme</span><span class="sxs-lookup"><span data-stu-id="9b161-154">Download DOC</span></span>](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|<span data-ttu-id="9b161-155">C# dil belirtimi Sürüm 1.0: Microsoft Corporation'ın</span><span class="sxs-lookup"><span data-stu-id="9b161-155">C# Language Specification Version 1.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="9b161-156">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="9b161-156">C# 1.2</span></span>|[<span data-ttu-id="9b161-157">Belge indirme</span><span class="sxs-lookup"><span data-stu-id="9b161-157">Download DOC</span></span>](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|<span data-ttu-id="9b161-158">C# dil belirtimi Sürüm 1.2: Microsoft Corporation'ın</span><span class="sxs-lookup"><span data-stu-id="9b161-158">C# Language Specification Version 1.2: Microsoft Corporation</span></span>|
|<span data-ttu-id="9b161-159">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="9b161-159">C# 2.0</span></span>|[<span data-ttu-id="9b161-160">PDF indirin</span><span class="sxs-lookup"><span data-stu-id="9b161-160">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|<span data-ttu-id="9b161-161">Standart ECMA 334 4 Edition</span><span class="sxs-lookup"><span data-stu-id="9b161-161">Standard ECMA-334 4th Edition</span></span>|
|<span data-ttu-id="9b161-162">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="9b161-162">C# 3.0</span></span>|[<span data-ttu-id="9b161-163">Belge indirme</span><span class="sxs-lookup"><span data-stu-id="9b161-163">Download DOC</span></span>](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|<span data-ttu-id="9b161-164">C# dil belirtimi sürüm 3.0: Microsoft Corporation'ın</span><span class="sxs-lookup"><span data-stu-id="9b161-164">C# Language Specification Version 3.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="9b161-165">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="9b161-165">C# 5.0</span></span>|[<span data-ttu-id="9b161-166">PDF indirin</span><span class="sxs-lookup"><span data-stu-id="9b161-166">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|<span data-ttu-id="9b161-167">Standart ECMA 334 5 Edition</span><span class="sxs-lookup"><span data-stu-id="9b161-167">Standard ECMA-334 5th Edition</span></span>|
|<span data-ttu-id="9b161-168">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="9b161-168">C# 6.0</span></span>|[<span data-ttu-id="9b161-169">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="9b161-169">Link</span></span>](../language-specification/index.md)|<span data-ttu-id="9b161-170">C# dil belirtimi sürüm 6 - resmi olmayan taslak: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="9b161-170">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span>|
|<span data-ttu-id="9b161-171">C# 7.0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="9b161-171">C# 7.0 and later</span></span>||<span data-ttu-id="9b161-172">Şu anda kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="9b161-172">not currently available</span></span>|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="9b161-173">Tüm dil özellikleri desteklemek için gereken en düşük derleyici sürümü</span><span class="sxs-lookup"><span data-stu-id="9b161-173">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="9b161-174">[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/derleme araçları .net 2002 veya ile birlikte gelen .net Framework 1.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="9b161-174">[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="9b161-175">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/derleme araçları 2005 veya ile birlikte gelen .net Framework 2.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="9b161-175">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="9b161-176">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/derleme araçları 2008 ya da ile birlikte gelen .net Framework 3.5 derleyici</span><span class="sxs-lookup"><span data-stu-id="9b161-176">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="9b161-177">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/derleme araçları 2010 veya ile birlikte gelen .net Framework 4.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="9b161-177">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="9b161-178">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/derleme araçları 2012 ya da ile birlikte gelen .net Framework 4.5 derleyici</span><span class="sxs-lookup"><span data-stu-id="9b161-178">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="9b161-179">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/derleme araçları 2015</span><span class="sxs-lookup"><span data-stu-id="9b161-179">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="9b161-180">[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/derleme araçları 2017</span><span class="sxs-lookup"><span data-stu-id="9b161-180">[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   
<span data-ttu-id="9b161-181">[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="9b161-181">[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>    
<span data-ttu-id="9b161-182">[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5</span><span class="sxs-lookup"><span data-stu-id="9b161-182">[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>    
<span data-ttu-id="9b161-183">[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15.7</span><span class="sxs-lookup"><span data-stu-id="9b161-183">[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
