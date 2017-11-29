---
title: "-langversion (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034958b14c54540aa175a23067d47bd5d850bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-c-compiler-options"></a><span data-ttu-id="63dbb-102">/langversion (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="63dbb-102">/langversion (C# Compiler Options)</span></span>
<span data-ttu-id="63dbb-103">Derleyicinin yalnızca seçilen C# dil belirtimi dahil sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="63dbb-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63dbb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63dbb-104">Syntax</span></span>  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="63dbb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="63dbb-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="63dbb-106">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="63dbb-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="63dbb-107">Seçenek</span><span class="sxs-lookup"><span data-stu-id="63dbb-107">Option</span></span>|<span data-ttu-id="63dbb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63dbb-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="63dbb-109">default</span><span class="sxs-lookup"><span data-stu-id="63dbb-109">default</span></span>|<span data-ttu-id="63dbb-110">Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="63dbb-110">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="63dbb-111"><sup id="TDefault">[Varsayılan](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="63dbb-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="63dbb-112">ISO-1</span></span>|<span data-ttu-id="63dbb-113">ISO/IEC 23270:2003 C# (1.0/1.1) dahil sözdizimi derleyici kabul <sup id="TISO1"> [ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="63dbb-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="63dbb-114">ISO-2</span></span>|<span data-ttu-id="63dbb-115">ISO/IEC 23270:2006 C# (2.0) dahil sözdizimi derleyici kabul <sup id="TISO2"> [ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="63dbb-116">3</span><span class="sxs-lookup"><span data-stu-id="63dbb-116">3</span></span>|<span data-ttu-id="63dbb-117">C# 3.0 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS3"> [CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="63dbb-118">4</span><span class="sxs-lookup"><span data-stu-id="63dbb-118">4</span></span>|<span data-ttu-id="63dbb-119">Derleyici dahil C# 4.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS4"> [CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="63dbb-120">5</span><span class="sxs-lookup"><span data-stu-id="63dbb-120">5</span></span>|<span data-ttu-id="63dbb-121">Derleyici dahil C# 5.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS5"> [CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="63dbb-122">6</span><span class="sxs-lookup"><span data-stu-id="63dbb-122">6</span></span>|<span data-ttu-id="63dbb-123">Derleyici dahil C# 6. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS6"> [CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="63dbb-124">7</span><span class="sxs-lookup"><span data-stu-id="63dbb-124">7</span></span>|<span data-ttu-id="63dbb-125">Derleyici dahil C# 7. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS7"> [CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="63dbb-126">en son</span><span class="sxs-lookup"><span data-stu-id="63dbb-126">latest</span></span>|<span data-ttu-id="63dbb-127">Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="63dbb-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="63dbb-128"><sup id="TLatest">[En son](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="63dbb-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="63dbb-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63dbb-129">Remarks</span></span>  
 <span data-ttu-id="63dbb-130">C# uygulamanız tarafından başvurulan meta veri değil tabi **/langversion** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="63dbb-130">Metadata referenced by your C# application is not subject to **/langversion** compiler option.</span></span>  
  
 <span data-ttu-id="63dbb-131">C# Derleyici her sürümü uzantıları dil belirtimi içerdiğinden **/langversion** Derleyici önceki bir sürümünü eşdeğer işlevselliğini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="63dbb-131">Because each version of the C# compiler contains extensions to the language specification, **/langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="63dbb-132">C# sürüm güncelleştirmelerini ile ana .net Framework sürümleri genellikle çakıştığı olsa da, ayrıca, özellikleri ve yeni sözdizimini mutlaka bu belirli framework sürümüne bağlı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="63dbb-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="63dbb-133">Yeni özelliklerin yanı sıra C# düzeltme de serbest yeni bir derleyici güncelleştirme kesinlikle gerektirir, ancak her belirli özellik kendi minimum .net API veya alt düzey çerçeveleri tarafından üzerinde çalışmasına izin verebilir ortak dil çalışma zamanı gereksinimleri vardır. NuGet paketlerini veya diğer kitaplıkları dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="63dbb-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="63dbb-134">Hangi **/langversion** ayarını kullanın, .exe veya .dll dosyası oluşturmak için geçerli ortak dil çalışma zamanı sürümünü kullanacak.</span><span class="sxs-lookup"><span data-stu-id="63dbb-134">Regardless of which **/langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="63dbb-135">Tek istisnası arkadaş derlemeleri ve [/moduleassemblyname (C# derleyici seçeneği)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), hangi altında çalışan **/langversion:ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="63dbb-135">One exception is friend assemblies and [/moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **/langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="63dbb-136">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="63dbb-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="63dbb-137">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="63dbb-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="63dbb-138">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="63dbb-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="63dbb-139">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="63dbb-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="63dbb-140">Değiştirme **dil sürümü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="63dbb-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="63dbb-141">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="63dbb-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="63dbb-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63dbb-142">See Also</span></span>  
 [<span data-ttu-id="63dbb-143">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="63dbb-143">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="63dbb-144">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="63dbb-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="63dbb-145">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="63dbb-145">C# Language Specification</span></span>
 <span data-ttu-id="63dbb-146">[C# dil belirtimi başvurusu](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="63dbb-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>  
 <span data-ttu-id="63dbb-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) bilgi teknolojisi--C# dil belirtimi: ISO Kataloğu</span><span class="sxs-lookup"><span data-stu-id="63dbb-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="63dbb-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) bilgi teknolojisi--C# dil belirtimi: ISO Kataloğu</span><span class="sxs-lookup"><span data-stu-id="63dbb-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="63dbb-149">C# 2.0 [c042926_ISO_IEC_23270_2006 (E) .zip](http://go.microsoft.com/fwlink/?LinkId=144406) PDF biçimli ISO/IEC 23270:2006: ISO serbestçe kullanılabilir standartları</span><span class="sxs-lookup"><span data-stu-id="63dbb-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>  
 <span data-ttu-id="63dbb-150">C# 3.0 [CSharp dil Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# dil belirtimi sürüm 3.0: Microsoft Corporation'ın</span><span class="sxs-lookup"><span data-stu-id="63dbb-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="63dbb-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) standart ECMA 334 4 Edition</span><span class="sxs-lookup"><span data-stu-id="63dbb-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="63dbb-152">C# 5.0 [CSharp dil Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# dil belirtimi Sürüm 5.0: Microsoft Corporation'ın</span><span class="sxs-lookup"><span data-stu-id="63dbb-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="63dbb-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# dil belirtimi sürüm 6 - resmi olmayan taslak: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="63dbb-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>  
 <span data-ttu-id="63dbb-154">C# 7.0 (şu anda kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="63dbb-154">C# 7.0 (not currently available)</span></span>  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="63dbb-155">Tüm dil özellikleri desteklemek için gereken en düşük derleyici sürümü</span><span class="sxs-lookup"><span data-stu-id="63dbb-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="63dbb-156">[↩](#TDefault)<a name="FDefault">varsayılan</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/derleme araçları .net 2002 veya ile birlikte gelen .net Framework 1.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="63dbb-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="63dbb-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/derleme araçları 2005 veya ile birlikte gelen .net Framework 2.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="63dbb-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="63dbb-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/derleme araçları 2008 ya da ile birlikte gelen .net Framework 3.5 derleyici</span><span class="sxs-lookup"><span data-stu-id="63dbb-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="63dbb-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/derleme araçları 2010 veya ile birlikte gelen .net Framework 4.0 derleyici</span><span class="sxs-lookup"><span data-stu-id="63dbb-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="63dbb-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/derleme araçları 2012 ya da ile birlikte gelen .net Framework 4.5 derleyici</span><span class="sxs-lookup"><span data-stu-id="63dbb-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="63dbb-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/derleme araçları 2015</span><span class="sxs-lookup"><span data-stu-id="63dbb-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="63dbb-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">son</a>: Microsoft Visual Studio/derleme araçları 2017</span><span class="sxs-lookup"><span data-stu-id="63dbb-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
