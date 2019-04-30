---
title: XAML Dili Ortak Temelleri İçin Yerleşik Türler
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: feda058a9672a3150f7beb5c1bc124eee1eae9eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689716"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="79f90-102">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="79f90-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="79f90-103">XAML 2009, ortak dil çalışma zamanı (CLR) ve diğer programlama dillerinde sık kullanılan temel eleman olan birkaç veri türü için XAML dili düzeyinde destek sunar.</span><span class="sxs-lookup"><span data-stu-id="79f90-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="79f90-104">XAML 2009 şu temelleri için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, ve `x:Array`</span><span class="sxs-lookup"><span data-stu-id="79f90-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="79f90-105">XAML biçimlendirmede dil temelleri için önceki teknikler</span><span class="sxs-lookup"><span data-stu-id="79f90-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="79f90-106">WPF önceki sürümleri için XAML içinde .NET Framework için CLR temel tanım sınıfı içeren ad alanı ve derleme eşleyerek CLR dil temellerine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f90-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="79f90-107">Bunların çoğu mscorlib derlemede ve <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="79f90-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="79f90-108">Örneğin, kullanılacak <xref:System.Int32>, aşağıdaki eşlemeyi (Bundan sonra gösterilen örnek kullanım ile) bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79f90-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="79f90-109">XAML 2009 dil temelleri</span><span class="sxs-lookup"><span data-stu-id="79f90-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="79f90-110">Kural gereği, XAML ve diğer tüm XAML dil öğeleri dil temelleri birlikte gösterilir `x:` önek.</span><span class="sxs-lookup"><span data-stu-id="79f90-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="79f90-111">Bu nasıl XAML dil öğeleri genellikle gerçek biçimlendirme içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79f90-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="79f90-112">Bu kural, WPF ve ayrıca XAML belirtiminde XAML için kavramsal belgelerinde izlenir.</span><span class="sxs-lookup"><span data-stu-id="79f90-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="79f90-113">x: nesne</span><span class="sxs-lookup"><span data-stu-id="79f90-113">x:Object</span></span>  
 <span data-ttu-id="79f90-114">CLR yedekleme `x:Object` karşılık gelen temel <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="79f90-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="79f90-115">Bu temel eleman uygulama biçimlendirme içinde genellikle kullanılmaz, ancak XAML türü sistemde atanabilirliği denetleme gibi bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="79f90-116">x: Boolean</span><span class="sxs-lookup"><span data-stu-id="79f90-116">x:Boolean</span></span>  
 <span data-ttu-id="79f90-117">CLR yedekleme `x:Boolean` karşılık gelen temel <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="79f90-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="79f90-118">XAML ayrıştırma değerlerini `x:Boolean` olarak büyük küçük harfe duyarlı.</span><span class="sxs-lookup"><span data-stu-id="79f90-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="79f90-119">Unutmayın `x:Bool` kabul edilen bir alternatif değildir.</span><span class="sxs-lookup"><span data-stu-id="79f90-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="79f90-120">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="79f90-121">x: Char</span><span class="sxs-lookup"><span data-stu-id="79f90-121">x:Char</span></span>  
 <span data-ttu-id="79f90-122">CLR yedekleme `x:Char` karşılık gelen temel <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="79f90-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="79f90-123">Dize ve karakter türlerinin XML düzeyinde dosyanın genel kodlama ile etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="79f90-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="79f90-124">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="79f90-125">x: String</span><span class="sxs-lookup"><span data-stu-id="79f90-125">x:String</span></span>  
 <span data-ttu-id="79f90-126">CLR yedekleme `x:String` karşılık gelen temel <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="79f90-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="79f90-127">Dize ve karakter türlerinin XML düzeyinde dosyanın genel kodlama ile etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="79f90-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="79f90-128">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="79f90-129">x: ondalık</span><span class="sxs-lookup"><span data-stu-id="79f90-129">x:Decimal</span></span>  
 <span data-ttu-id="79f90-130">CLR yedekleme `x:Decimal` karşılık gelen temel <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="79f90-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="79f90-131">XAML ayrıştırma altında kendiliğinden yapıldığına olduğunu unutmayın `en-US` kültür.</span><span class="sxs-lookup"><span data-stu-id="79f90-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="79f90-132">Altında `en-US` kültür, ondalık sayı bileşenleri için doğru ayırıcı her zaman bir noktadır (`.`) geliştirme ortamının veya XAML çalışma zamanında yüklendiği nihai istemci hedef kültür ayarları ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="79f90-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="79f90-133">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="79f90-134">x: Single</span><span class="sxs-lookup"><span data-stu-id="79f90-134">x:Single</span></span>  
 <span data-ttu-id="79f90-135">CLR yedekleme `x:Single` karşılık gelen temel <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="79f90-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="79f90-136">İçin metin sözdizimi sayısal değerlere ek olarak `x:Single` ayrıca belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`.</span><span class="sxs-lookup"><span data-stu-id="79f90-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="79f90-137">Bu belirteçleri olarak büyük küçük harfe duyarlı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="79f90-138">`x:Single` metin sözdiziminin ilk karakteri ise değerleri bilimsel gösterim biçiminde destekleyebilir `e` veya `E`.</span><span class="sxs-lookup"><span data-stu-id="79f90-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="79f90-139">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="79f90-140">x: Double</span><span class="sxs-lookup"><span data-stu-id="79f90-140">x:Double</span></span>  
 <span data-ttu-id="79f90-141">CLR yedekleme `x:Double` karşılık gelen temel <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="79f90-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="79f90-142">İçin metin sözdizimi sayısal değerlere ek olarak `x:Double` belirteçlerine izin verir `Infinity`, `-Infinity`, ve `NaN`.</span><span class="sxs-lookup"><span data-stu-id="79f90-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="79f90-143">Bu belirteçleri olarak büyük küçük harfe duyarlı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="79f90-144">`x:Double` değerleri bilimsel gösterim biçiminde destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="79f90-145">Karakter kullanın `e` veya `E` üs bölümü tanıtmak için.</span><span class="sxs-lookup"><span data-stu-id="79f90-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="79f90-146">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="79f90-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="79f90-147">x:Int16</span></span>  
 <span data-ttu-id="79f90-148">CLR yedekleme `x:Int16` karşılık gelen temel <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="79f90-149">XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="79f90-150">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="79f90-151">x: Int32</span><span class="sxs-lookup"><span data-stu-id="79f90-151">x:Int32</span></span>  
 <span data-ttu-id="79f90-152">CLR yedekleme `x:Int32` karşılık gelen temel <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="79f90-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="79f90-153">`x:Int32` işaretlenmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="79f90-154">XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="79f90-155">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="79f90-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="79f90-156">x:Int64</span></span>  
 <span data-ttu-id="79f90-157">CLR yedekleme `x:Int64` karşılık gelen temel <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="79f90-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="79f90-158">`x:Int64` işaretlenmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="79f90-159">XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.</span><span class="sxs-lookup"><span data-stu-id="79f90-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="79f90-160">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="79f90-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="79f90-161">x:TimeSpan</span></span>  
 <span data-ttu-id="79f90-162">CLR yedekleme `x:TimeSpan` karşılık gelen temel <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="79f90-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="79f90-163">Bu XAML ayrıştırma için saat ve tarih biçimi altında kendiliğinden yapıldığına dikkat edin `en-US` kültür.</span><span class="sxs-lookup"><span data-stu-id="79f90-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="79f90-164">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="79f90-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="79f90-165">x:Uri</span></span>  
 <span data-ttu-id="79f90-166">CLR yedekleme `x:Uri` karşılık gelen temel <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="79f90-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="79f90-167">Protokollerin denetimi için XAML tanımının bir parçası değil `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="79f90-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="79f90-168">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="79f90-169">x: Byte</span><span class="sxs-lookup"><span data-stu-id="79f90-169">x:Byte</span></span>  
 <span data-ttu-id="79f90-170">CLR yedekleme `x:Byte` karşılık gelen temel <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="79f90-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="79f90-171">A <xref:System.Byte>  /  `x:Byte` değerlendirilir işaretlenmemiş olarak.</span><span class="sxs-lookup"><span data-stu-id="79f90-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="79f90-172">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="79f90-173">x: Array</span><span class="sxs-lookup"><span data-stu-id="79f90-173">x:Array</span></span>  
 <span data-ttu-id="79f90-174">CLR yedekleme `x:Array` karşılık gelen temel <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="79f90-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="79f90-175">Biçimlendirme uzantısı sözdizimi kullanarak XAML 2006'da dizi tanımlayabilirsiniz; Ancak, XAML 2009 biçimlendirme uzantısına erişmesi gerekmeyen dil tanımlı temel sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="79f90-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="79f90-176">XAML 2006 desteği hakkında daha fazla bilgi için bkz. [x: Array işaretleme uzantısı](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="79f90-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="79f90-177">XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="79f90-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="79f90-178">WPF desteği</span><span class="sxs-lookup"><span data-stu-id="79f90-178">WPF Support</span></span>  
 <span data-ttu-id="79f90-179">WPF içinde ancak yalnızca işaretleme yapılmayan XAML için XAML 2009 özelliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f90-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="79f90-180">WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="79f90-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="79f90-181">XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz senaryo gevşek XAML yazar ve sonra içine bir WPF çalışma zamanı ve Nesne grafiği ile XAML yük olan <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79f90-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="79f90-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve kendi <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcükleri ve özellikleri bir geçerli nesne grafiği gösterimi halinde işler.</span><span class="sxs-lookup"><span data-stu-id="79f90-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
